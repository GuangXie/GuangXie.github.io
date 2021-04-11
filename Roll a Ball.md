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

    目标2：使用Inputs System获取玩家的键盘输入，来实现球体的移动。
```C#
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.InputSystem;

    public class PlayerController:MonObehaviour
    {
        void Start()
        {

        }

        void OnMove()
        {

        }
    }
 ```

