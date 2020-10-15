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
