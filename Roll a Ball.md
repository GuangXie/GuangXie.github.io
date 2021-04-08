# Roll a Ball 学习
## **1.移动玩家**
    目标：获取玩家的键盘输入，然后将输入转换成对球体的作用力，来实现球体的移动。
```C#
public class PlayerController:MonObehaviour
{
    //创建公共变量seppd来控制力的大小，且可以在脚本面版直接修改seppd的参数。
    public float speed;

    private Rigidbody rb;

    void Start ()
    {
         //创建变量持有刚体引用
        rb = GetComponent<Rigidbody>();
    }

    void FixedUpdate()
    {
        //获取水平轴和垂直轴
        float moveHorizontal = Input.GetAxis("Horizontal");
        float moveVertical = Input.GetAxis("Vertical");

        Vector3 movement = new Vector3(moveHorizontal,0.0f,moveVertical);

        rb.AddForec(movement * speed);
    }
}

```
使用方法：Input.GetAxis与以下默认轴配合使用： “**Horizontal**”* 和"**Vertical**"映射键盘按键（A、S、D、W和方向键）；"**Mouse X**"和"**Mouse Y**"映射鼠标左右键；"**Fire1**"、"**Fire2**"、"**Fire3**"映射Ctrl、Alt、Cmd键和三键鼠标或游戏手柄按钮。

