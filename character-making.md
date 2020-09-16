# 問題が起きにくいキャラクターの作り方


親子階層を作る！
一番上のオブジェクト(Hierarchy直下)・・・移動や当たり判定担当
操作用のスクリプトを貼り付ける
RigidbodyやColliderを持つこと
Unityで手付けするアニメはこちら
子供のオブジェクト・・・見た目担当
モデルを持つこと
モデルにつけたアニメーションはこちら
モデルが向いている方向と、一番上のオブジェクトが向いている方向を一致させる
スケールを調整（なるべくモデルの読み込み設定でやるのがよい)
見た目と当たり判定を分けて考えると柔軟なシステムが作れる

親のオブジェクトを作る
HierarchyウィンドウのCreateをクリックして、Create Emptyで空のゲームオブジェクトを作る
Playerなどの名前にしておくと分かりやすい
ProjectウィンドウのStandard Assetsフォルダーを開いて、Vehicles > Aircraft > Modelsを開く
モデルが3つあるので、どれがクリックして選択
Inspectorウィンドウで、Modelボタンをクリック
Scale Factorで、モデルの大きさを変更できる
Import Camerasのチェックを外すと、モデリングツールで設定したカメラを読み込まない。チェックを外しておくのが一般的
Import Lightsも同様に、ライトを読み込まない。チェックを外しておくのが一般的
上記、設定を変更したら、Applyボタンをクリックして反映
AircraftFuselageをドラッグして、Playerにドロップ
親のゲームオブジェクトはそのままで、見せたい方向と座標に調整する
大きさは、Scaleで確認してから、モデルのScaleファクターで調整した方がよい
子供のオブジェクトは、親を基準に動いたり、回転したり、拡大縮小する
相対的にふるまう=local(ローカル)
親からの座標や回転を知りたい場合、transform.localPosition / transform.localRotation / transform.localScale
親はワールド座標系に従う
絶対的にふるまう
localPositionとpositionは一致

シューティング的なやつの自機を作ってみる
WindowメニューからAsset Storeを選択
Standardで検索
Standard Assets(Unity製)が見つかるのでクリック
インポートして、Import

動かし方
Unityに当たり判定を任せる場合、transform.positionに直接次の座標を代入したり、transform.Translate()を使うことはない！！ = ワープしてしまうので、物理演算が正しく行えない
初期座標を設定したり、実際にワープする時に上記を使う

必要なコンポーネントを追加する
Rigidbodyか、Rigidbody2Dか、CharacterController
CharacterControllerは、斜面を登ったり、ジャンプしたりするキャラクター向け
決まった角度までの斜面を登れる
決まった高さの段差は自動的に越える
着地判定を自動的にやってくれる(isGrounded)
上記以外のものは、3DならRigidbody、2DならRigidbody2Dを入れる
当たり判定などを、全部自作する場合のみ、上記がいらない

今回はRigidbodyをアタッチ
Playerをクリック(おやのオブジェクト)
Add Componentをクリックして、Physics > Rigidbodyを選択
Rigidbodyの設定
Use Gravity＝重力を使うかどうか。重力落下が不要ならチェックを外す
Constraints＝移動や回転を固定するための設定。使わない移動軸や回転軸は、チェックを入れて固定しておいた方が安定して動く

操作スクリプトを作成
Add ComponentからNew scriptをクリックして、Playerと入力してEnterキーを押す
Playerスクリプトをダブルクリックして開く



移動にはRigidbodyのvelocityを使う！！

Rigidbodyでオブジェクトを動かす方法
最初に、Rigidbodyのインスタンス(Rigidbodyを操作するためのデータ)を取得する
7行目付近に、以下を追加

    Rigidbody rb;

void Start()をvoid Awake()に変更して、以下を入力

    void Awake()
    {
        rb = GetComponent<Rigidbody>();
    }

以上で、rbを使えば、PlayerにアタッチしたRigidbodyコンポーネントを操作できる。

仮に上に移動させてみる。Awakeの最後に、以下を追加して、Unityで実行してみる。

rb.velocity = Vector3.up;

上方向に、秒速1mの速さで移動する

速さを変えたい場合、単位ベクトル(長さ1のベクトル)に、速さをかける。

rb.velocity = Vector3.up*5f;

プレイヤーのキー操作
方向(上下左右)の入力を使いたい場合、Input.GetAxis()、あるいは、Input.GetAxisRaw()を使うのがおすすめ！

GetAxis()は、矢印キーなどを押した場合に、アナログスティックっぽく徐々に数値が変化する
GetAxisRaw()は、矢印キーなどのデジタル入力は、押したら1、離したら0にすぐになる
2Dのシューティングのようなキビキビ動かしたい場合はGetAxisRaw()を使う

Input.GetAxisRaw(“Horizontal”)とやると、左を押すと-1、右を押すと1、離すと0
Input.GetAxisRaw(“Vertical”)とやると、上を押すと1、下を押すと-1、離すと0

Update()内に以下を実装する。

rb.velocityなどには、rb.velocity.x = 0; などのように、個別に値を設定できない！！
一度、設定用のベクトルを宣言して、それに代入したい値を設定して、rb.velocityに代入する。

    void Update()
    {
        Vector3 move = rb.velocity;
        move.x = Input.GetAxisRaw("Horizontal");
        move.y = Input.GetAxisRaw("Vertical");
        rb.velocity = move * 5f;
    }

斜めの速度を同じにする
moveを正規化してから、速度を掛ける
正規化とは・・・長さを１にすること＝normalize
rb.velocityの式のmoveに、以下のように「.normalized」をくっつければ解決！

        rb.velocity = move.normalized * 5f;

当たり判定の考え方
Unityでは、Rigidbody(剛体)のシミュレーションを使う
Rigidbodyは、現在の速度(velocity)を設定すると、自動的に物理演算をして、移動、および、当たり判定をしてくれる
親のオブジェクトに、？？Colliderをアタッチする
SphereCollider=球体。一番軽い
BoxCollider=立方体。軽い
CapsuleCollider=カプセル状。BoxColliderほどではないが軽い
MeshCollider=モデルの形状。重い。動かす場合、Convexにチェック

今回は、やや縦長にしたいので、BoxColliderを利用
親のオブジェクトに、Add Componentで、Physics > Box Colliderを選択
緑色の枠が、当たり判定。これを、CenterとかSizeとかでちょうどよい形に整える=Scaleでは調整しないこと！！






ぶつかる相手を作成
HierarchyウィンドウのCreateをクリックして、3D Object > Sphere
名前をItemに変更して、適当な場所へ移動
Rigidbodyをアタッチして、必要に応じて、Is TriggerとUse Gravityのチェックを設定する。とりあえず、Is Triggerにチェック


プレイヤーや敵を、外に出さない設定
Cubeを4つ作成して、配置とScaleでサイズを調整して、画面を取り巻くようにする
MeshRendererのチェックをはずせば、四角は表示されなくなる。当たり判定は残る

OnCollisionEnter()とOnTriggerEnter()
OnCollisionEnter()は、衝突して跳ね返ったりした時に呼ばれる
OnTriggerEnter()は、お互いに干渉はしないが、当たり判定が重なった時に呼ばれる
？？ColliderコンポーネントのIs Triggerにチェックをいれる

Itemを取れるようにする
アイテムには、衝突する必要はないので、Triggerを使う
スクリプトは、プレイヤーに付ける？Itemに付ける？
色々な設定が必要な方にアタッチする
必要なら、両方に付ける
やりたいことを整理すれば自然と判明
アイテムを消す
将来的に、効果音を鳴らす
将来的に、スコアを加算
アイテムにItemスクリプトをnew Scriptでアタッチ
Itemスクリプトをダブルクリック。Start()とUpdate()は消していい
「void OnT」ぐらい入力すると、OnTriggerEnterが見つかるので、選択すればよい
トリガーが発生した時に、Unityが、自動的にOnTriggerEnterを呼び出す
衝突相手の情報が、otherに入っているので、誰と接触したかを、other.CompareTag(タグ名)で識別できる

Unityでは、何とぶつかったかなどを判別するために、Tagを使う。

Playerオブジェクトに、Playerタグを設定しておく






Playerに衝突したら、消す
OnTriggerEnter()を以下のようにする


    private void OnTriggerEnter(Collider other)
    {
        // 相手がPlayerか？
        if (other.CompareTag("Player"))
        {
            // 自分自身を消す
            Destroy(gameObject);
        }
    }

動きを確認したら、ItemのUse Gravityのチェックを外す


オブジェクトの生成(Instantiate)
ゲームオブジェクトか、プレハブを元に、プログラムでオブジェクトを生成できる

オブジェクトを生成するためのオブジェクト(Spawner)を作るとよい。

HierarchyウィンドウのCreateをクリックして、Create Emptyで空のゲームオブジェクトを作成して、名前をSpawnerにする
Add Componentをクリックして、New scriptをクリックして、Spawnerの名前でEnterキーを押す

開始と同時に、指定したオブジェクトを、指定した数だけ、指定した範囲にランダムで出現させる。

必要なパラメーターを定義する。Unityから設定できるようにする。

7行目あたりに以下を追加する

    [SerializeField]
    GameObject item = null;
    [SerializeField]
    int spawnCount = 10;
    [SerializeField]
    Vector3 spawnRange = new Vector3(5, 3, 0);


[SerializeField]とは？
　UnityのInspectorにパラメーターを公開する時に使う属性。
　publicにしてもよいが、publicだと他のクラスから読み書きができるので、それが不要な場合は[SerializeField]を使う方がよい。

注意！！
publicや[SerializeField]でUnityに公開したパラメーターは、ソースコードの変更では、値が反映されない！！

オブジェクトを生成
Itemをプレハブ化したら、Hierarchyから削除
HierarchyウィンドウのSpawnerオブジェクトをクリックして選択
ProjectウィンドウのItemプレハブドラッグして、InspectorのItem欄にドロップ
SpawnerスクリプトのStartに以下を追加。まずは1匹作成

    void Start()
    {
        Vector3 pos = new Vector3(
            Random.Range(-spawnRange.x, spawnRange.x),
            Random.Range(-spawnRange.y, spawnRange.y),
            0
            );
        Instantiate(item, pos, Quaternion.identity);
    }






