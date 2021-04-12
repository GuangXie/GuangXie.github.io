# Roll a Ball 学习
## **一.移动玩家**
    目标1：获取玩家的键盘输入，然后将输入转换成对球体的作用力，来实现球体的移动。
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerController:MonObehaviour
{
    //创建公共变量seppd来控制力的大小，且可以在脚本面版直接修改seppd的参数。
    public float speed;

    private Rigidbody rb;

    void Start ()
    {
         //创建变量rb获得刚体引用
        rb = GetComponent<Rigidbody>();
    }

    void FixedUpdate()
    {
        //创建变量获得键盘输入的水平轴和垂直轴
        float moveHorizontal = Input.GetAxis("Horizontal");
        float moveVertical = Input.GetAxis("Vertical");

        //创建一个Vector3三维向量
        Vector3 movement = new Vector3(moveHorizontal,0.0f,moveVertical);

        rb.AddForec(movement * speed);
    }
}

```
备注：Input.GetAxis与以下默认轴配合使用： “**Horizontal**”* 和"**Vertical**"映射键盘按键（A、S、D、W和方向键）；"**Mouse X**"和"**Mouse Y**"映射鼠标左右键；"**Fire1**"、"**Fire2**"、"**Fire3**"映射Ctrl、Alt、Cmd键和三键鼠标或游戏手柄按钮。

## **二.移动摄像机**
```C#
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public GameObject player;

    privat Vector3 offset;

    public class GameraController:MonObehaviour
    {
        void Start()
        {
            //用摄像机的position值减去玩家的position值得到偏差值offset
            offset = transform.position - player.transform.position;
        }

        void LateUpdate()
        {
            //在游戏的每一帧都让摄像机的position值加上偏差值offset，这样当角色移动，在每一帧摄像机展示拍摄画面之前，摄像机都会先移动到跟角色相关的新位置
            transform.position = player.transform.position + offset;
        }
    }
 ```
 备注：使用LateUpdate可以确保玩家移动后，摄像机再移动到玩家当前位置

 ## **三.设置收集物**
 1.将方块收集物的transform组件rotation属性中的XYZ均修改为45，使方块倾斜，并在编写脚本使方块旋转。
 ```C#
public class Rotator:MonObehaviour
{
    void Update()
    {
        transform.Rotate(new Vector(15,30,45) * Time.daltaTime);
    }
}

//在玩家脚本中添加如下代码实现当玩家碰撞到收集物时，收集物消失。
private void OnTriggerEnter(Collider other)
    {
        Destroy(other.gameObject);
    }
 ```

