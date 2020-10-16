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
