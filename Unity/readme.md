# GameObject
- componentの集合体
- tagつけて探しやすくする、IDみたいなもの

# Transform
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Manager : MonoBehaviour {
    Vector3 rotation;
    // publicにするとinspectorに現れるが、どのクラスからもアクセスできる
    // privateにして[SerializeField]をつける
    [SerializeField]
    private GameObject target;

    private void Start() {
        rotation = this.transform.eulerAngles;
    }

    // Update is called once per frame
    // 1 sec = 60 frame
    void Update() {
        if (Input.GetKey(KeyCode.W)) {
            // 移動させる
            // 1秒単位で動かす場合はTime.deltaTimeをかける
            // thisはこのスクリプトがくっついたGameObjectを指す
            // this.[コンポネント].[要素]
            // positionはVector3(x,y,z)を持つ
            this.transform.position = this.transform.position + new Vector3(0, 0, 1) * Time.deltaTime;

            // Translate使うやり方
            this.transform.Translate(new Vector3(0,0,1) * Time.deltaTime);

            // 90度回転させる
            rotation = rotation + new Vector3(90, 0, 0) * Time.deltaTime;
            this.transform.eulerAngles = rotation;
            Debug.Log(transform.eulerAngles);

            // 90超えてもカクカクにならない
            this.transform.Rotate(new Vector3(90, 0, 0) * Time.deltaTime);

            // もっと正確に回転させたいときはQuaternion使う
            this.transform.rotation = Quaternion.Euler(new Vector3(90, 0, 0) * Time.deltaTime);

            // 大きさ
            this.transform.localScale = this.transform.localScale + new Vector3(2, 2, 2) * Time.deltaTime;

            // 指定した方向を見る関数
            this.transform.LookAt(target.transform.position);

            // 指定したオブジェクトを中心に回る
            this.transform.RotateAround(target.transform.position, Vector3.up, 100 * Time.deltaTime);
        }
    }
}
```

# RigidBody
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class RigidBody : MonoBehaviour
{
    private Rigidbody rigid;

    // Start is called before the first frame update
    void Start()
    {
        rigid = GetComponent<Rigidbody>();
        // 物理効果を有効
        rigid.isKinematic = false;
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetKey(KeyCode.W)) {
            // 速度
            //rigid.velocity = Vector3.forward;// new Vector3(0, 0, 1);と同じ意味

            // 最大回転速度(default = 7)
            rigid.maxAngularVelocity = 100;
            // 回転速度
            rigid.angularVelocity = Vector3.right;// -Vector3.rightは左

            // MoveXXXは物理効果は関係ない
            rigid.MovePosition(transform.forward * Time.deltaTime);

            // 移動
            rigid.AddForce(Vector3.forward);

            // 回転を維持しながらゆっくり止まる
            rigid.AddTorque(Vector3.up);

            // 右から爆発させる
            rigid.AddExplosionForce(10, this.transform.right, 10);
	    }
    }
}
```

# Box Collider
- Collider同士で衝突する
- MaterialにPhisycs Materialをアタッチすると跳ねる
- Is Triggerは衝突を感知するだけで、通過する（イベント用）

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Collider : MonoBehaviour
{
    private BoxCollider box;

    // Start is called before the first frame update
    void Start()
    {
        box = GetComponent<BoxCollider>();
    }

	// Update is called once per frame
	void Update()
	{
		// GetKeyDownは一度だけ
		if (Input.GetKeyDown(KeyCode.W))
		{
			Debug.Log("bounds " + box.bounds);
			Debug.Log("bounds extends " + box.bounds.extents);
			Debug.Log("bounds extends x" + box.bounds.extents.x);
			Debug.Log("box size " + box.size);
			Debug.Log("box center " + box.center);
		}

		// left click
		if (Input.GetMouseButtonDown(0))
		{
			Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
			RaycastHit hitInfo;
			if (box.Raycast(ray, out hitInfo, 1000))
			{
				this.transform.position = hitInfo.point;
			}
		}
	}

	private void OnTriggerStay(UnityEngine.Collider other)
	{
        other.transform.position += new Vector3(0, 0, 0.01f);
	}

	private void OnTriggerExit(UnityEngine.Collider other)
	{
		other.transform.position = new Vector3(0, 2, 0);
	}
}
```

# MeshRenderer
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Mesh : MonoBehaviour
{
    [SerializeField]
    private Material red;
    [SerializeField]
    private Material green;
    private MeshRenderer mesh;

    // Start is called before the first frame update
    void Start()
    {
        mesh = GetComponent<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        if (Input.GetMouseButtonDown(0)) {
            mesh.material = red;
        } else {
            mesh.material = green;
        }
    }
}
```

# Camera
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class MainCamera : MonoBehaviour
{
    [SerializeField]
    private GameObject target;

    [SerializeField]
    private float speed;

    private Vector3 diff;

    // Start is called before the first frame update
    void Start()
    {
        diff = transform.position - target.transform.position;
        diff = new Vector3(Mathf.Abs(diff.x), Mathf.Abs(diff.y), Mathf.Abs(diff.z));
    }

    // Update is called once per frame
    void Update()
    {
        // 動きを滑らか
        this.transform.position = Vector3.Lerp(this.transform.position, target.transform.position + diff, speed);
    }
}
```

# ゲームオブジェクトのLifeCycle
Awake
初期化
OnEnable
ゲームオブジェクトが活性化
Start
初期化

FixedUpdate
固定回数
Update
環境によって違う(1sec = 60frame)
LateUpdate
すべてのUpdateが終わってから

OnDestroy
ゲームオブジェクトが削除される前
OnDisable
ゲームオブジェクトが非活性化

# Input
Input.anyKeyDown   押したときTRUE
Input.anyKey  どんなキーでもいい、押してる間TRUE

# SpriteRenderer
- 画像のTexture TypeがSprite(2D and UI)になってないとSpriteRendererのSpriteに代入できない

# GameObjectの移動
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{
    private float speed = 5.0f;
    private Vector3 direction = Vector3.zero;

    // Start is called before the first frame update
    void Awake()
    {
        // vector3方向 * 速度
        transform.position = transform.position + new Vector3(1, 0, 0) * 1;
        // transform.position += Vector3.right * 1;
    }

    private void Update()
    {
        // -1:left 1:left 0:none
        float x = Input.GetAxisRaw("Horizontal");
        // -1:down 1:up 0:none
        float y = Input.GetAxisRaw("Vertical");

        direction = new Vector3(x, y, 0);

        transform.position += direction * speed * Time.deltaTime;
    }
}
```

# GameObjectの衝突
- 二つのオブジェクトがCollider2Dを持ってること
- 一つ以上のオブジェクトがRigidBodyを持ってること

- OnTriggerEnterで判定する場合は、Colliderコンポーネント内のisTriggerにチェックをつけて置く必要
- OnCollisionEnterは衝突した際の反発がある際に発火するので、Colliderコンポーネント内のisTriggerにチェックは外し
反発させるためには、判定したいオブジェクトにRigiBodyコンポーネントを追加して置く必要

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Player : MonoBehaviour
{
    private float moveSpeed = 5.0f;
    private Rigidbody2D rigid;

    // Start is called before the first frame update
    void Awake()
    {
        rigid = GetComponent<Rigidbody2D>();
    }

    // Update is called once per frame
    void Update()
    {
        float x = Input.GetAxisRaw("Horizontal");
        float y = Input.GetAxisRaw("Vertical");

        rigid.velocity = new Vector3(x, y, 0) * moveSpeed;
    }
}

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class TriggerEvent : MonoBehaviour
{
    [SerializeField]
    private GameObject moveObject;
    [SerializeField]
    private Vector3 moveDirection;
    private float moveSpeed;

    // Start is called before the first frame update
    void Awake()
    {
        moveSpeed = 5.0f;
    }

	private void OnTriggerEnter2D(Collider2D collision)
	{
        moveObject.GetComponent<SpriteRenderer>().color = Color.black;
	}

	private void OnTriggerStay2D(Collider2D collision)
	{
        moveObject.transform.position += moveDirection * moveSpeed * Time.deltaTime;
	}

	private void OnTriggerExit2D(Collider2D collision)
	{
        moveObject.GetComponent<SpriteRenderer>().color = Color.white;
        moveObject.transform.position = new Vector3(0,2,0);
	}
}
```

# Prefab
Hierarchyにひな形のGameObject生成
Assetsにドラッグ（青いボックスアイコン）
HierarchyのGameObjectを消す
空のオブジェクト作って、ObjectFactoryスクリプトをあてる

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ObjectFactory : MonoBehaviour
{
    [SerializeField]
    private GameObject prefab;

    // Start is called before the first frame update
    void Awake()
    {
        // 45度回転
        Quaternion rotation = Quaternion.Euler(0, 0, 45);
        Instantiate(prefab, new Vector3(2, 3, 0), rotation);
        // 回転なし
        GameObject clone = Instantiate(prefab, new Vector3(-2, 3, 0), Quaternion.identity);
        // 作ったオブジェクトを変更
        clone.name = "CloneObj";
        clone.GetComponent<SpriteRenderer>().color = Color.black;
        clone.transform.position = new Vector3(2, 1, 0);
        clone.transform.localScale = new Vector3(3, 2, 1);
    }
}
```
