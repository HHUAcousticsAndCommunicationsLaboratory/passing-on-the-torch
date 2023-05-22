# Unity文档语法笔记

*前言：此笔记本不是给正常人看的，只是为了锻炼我自己的英语看的*

## Instantiate

> 链接：[Unity - Scripting API: Object.Instantiate](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Object.Instantiate.html)

这玩意应该是用来copy的，它返回一个**Object** The instantiated clone.

了解几个英文：Transform转换矩阵，包含Position, rotation and scale of an object.

就是这么个东西：<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230519200531882.png" alt="image-20230519200531882" style="zoom:50%;" />

几个重载：<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230519200846684.png" alt="image-20230519200846684" style="zoom:50%;" />

关于参数Parameters

original-你想复制的对象；position-新对象的位置；rotation-新物体的角度；parent-分配给新物体的父对象；instantiatedInWorldSpaces是一个布尔值，这是它的解释：

如果将instantiateInWorldSpace设置为true,则新创建的游戏对象将被放置在当前场景的世界空间中。这意味着它的位置、旋转和缩放将与场景中的其他对象相对应。

如果将instantiateInWorldSpace设置为false,则新创建的游戏对象将被放置在当前场景的本地坐标系中。这意味着它的位置、旋转和缩放将相对于场景中的其他对象进行计算，而不是相对于整个世界空间。（在这里是相对它的父对象）

When this method clones a child object, it also clones the child's own children. To prevent stack overflow, Unity limits this nested cloning. If you exceed more than half your stack size, Unity throws an .

Note:

- By default the *parent* of the new object is null; it is not a "sibling" of the original. However, you can still set the parent using the overloaded methods. If a parent is specified and no position and rotation are specified, the original object's position and rotation are used for the cloned object's local position and rotation, or its world position and rotation if the parameter is true. If the position and rotation are specified, they are used as the object's position and rotation in world space.
- The active status of a GameObject at the time of cloning is maintained, so if the original is inactive the clone is created in an inactive state too. Additionally for the object and all child objects in the hierarchy, each of their Monobehaviours and Components will have their Awake and OnEnable methods called only if they are active in the hierarchy at the time of this method call.
- These methods do not create a prefab connection to the new instantiated object. Creating objects with a prefab connection can be achieved using [PrefabUtility.InstantiatePrefab](https://docs.unity.cn/2021.3/Documentation/ScriptReference/PrefabUtility.InstantiatePrefab.html).

```c#
        for (int i = 0; i < 10; i++)
        {
            Instantiate(prefab, new Vector3(i, (3 * i - 2), (2 * i - 1)), Quaternion.identity);
        }//很神奇，比起直接拖拽创建多个prefab，它能通过代码瞬间创建多个prefab，并且在结束游戏后这些实例全都消失了
```

关于Quaternion.identity：当使用Quaternion.identity时，它会返回一个四元数，其w、x、y和z值均为0,这意味着它表示一个指向原点的旋转坐标系。因此，将这个四元数与任何向量相乘都会得到一个相对于坐标系原点的方向和大小的向量。通常情况下，我们会在游戏对象被创建时将其初始化为Quaternion.identity,以便后续对其进行旋转操作时能够方便地指定旋转中心。

当然，如果这个原始角色是一个浮在空中的球，那么将会很有趣，像这个鸟样

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230519210954019.png" alt="image-20230519210954019" style="zoom:50%;" />

再来一段代码



```c#
using UnityEngine;

public class TestPrefab : MonoBehaviour
{
    public Rigidbody rb;
    Vector3 OnePosition;
    Quaternion Rotation;
    // Start is called before the first frame update
    void Start()
    {
        OnePosition = rb.transform.position;
        Rotation=rb.transform.rotation;
    }

    // Update is called once per frame
    void Update()
    {
        //如果你想要检测用户当前是否正在按下某个按钮，应该使用Input.GetButton;
        //如果你想要检测用户之前是否已经按下了某个按钮，应该使用Input.GetButtonDown。
        if (Input.GetButtonDown("Fire1"))//这里有个GetButton和GetButtonDown的区别
         //fire1是按下ctrl，这在 Edit > Project Settings > Input Manager
         //草点击鼠标也是可以的
        {
            //我这里设置的克隆位置和初始对象的一样，就是为了一个撒尿的效果
            Rigidbody clone = Instantiate(rb, OnePosition, Rotation);
            clone.velocity = transform.TransformDirection(Vector3.forward * 10);
        }
    }
}
```

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230520083012819.png" alt="image-20230520083012819" style="zoom:50%;" />

这里就涉及到几个函数了，咱们展开讲一下

---

#### 1.Input.GetButton()与Input.GetButtoDown()

> GetButton链接：[Unity - Scripting API: Input.GetButton](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Input.GetButton.html)
>
> GetButtonDown链接：[Unity - Scripting API: Input.GetButtonDown](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Input.GetButtonDown.html)

如果你想要检测用户当前是否正在按下某个按钮，应该使用Input.GetButton()
如果你想要检测用户之前是否已经按下了某个按钮，应该使用Input.GetButtonDown()

简单来说，GetButton就是用的全自动机关枪，而GetButtonDown是半自动机关枪

这是关于GetButtonDown的英文描述：

> Returns true during the frame the user pressed down the virtual button identified by .`buttonName`
>
> Call this function from the [Update](https://docs.unity.cn/2021.3/Documentation/ScriptReference/MonoBehaviour.Update.html) function, since the state gets reset each frame(since这句是描述update的). **It will not return true until the user has released the key and pressed it again**.（在用户松开前是不会返回true值）

To edit, set up, or remove buttons and their names (such as "Fire1"): 

1. Go to **Edit** > **Project Settings** > **Input Manager** to bring up the Input Manager.
2. Expand **Axis** by clicking the arrow next to it. This shows the list of the current buttons you have. You can use one of these as the parameter "buttonName". 
3.  Expand one of the items in the list to access and change aspects such as the button's name and the key, joystick or mouse movement that triggers it. 
4.  For more information about buttons, see the [Input Manager](https://docs.unity.cn/2021.3/Documentation/Manual/class-InputManager.html) page.

这是全自动GetButton<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230520113727779.png" alt="image-20230520113727779" style="zoom:50%;" />

这是关于GetButton的描述

> ### Returns
>
> **bool** True when an axis has been pressed and not released.
>
> ### Description
>
> Returns true while the virtual button identified by `buttonName` is held down.
>
> Think auto fire - this will return true as long as the button is held down. Use this only when implementing events that trigger an action, eg, shooting a weapon. The `buttonName` argument will normally be one of the names in [InputManager](https://docs.unity.cn/2021.3/Documentation/Manual/class-InputManager.html) such as Jump or Fire1. [GetButton](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Input.GetButton.html) will return to `false` when it is released.
>
> **Note:** Use [GetAxis](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Input.GetAxis.html) for input that controls continuous movement.

#### 2. RigidBody.velocity

​	刚体的速度矢量。它表示刚体位置的变化率。

In most cases you should not modify the velocity directly, as this can result in unrealistic behaviour - use AddForce instead (不要直接改速度，会失真)

Do not set the velocity of an object every physics step, this will lead to unrealistic physics simulation. A typical usage is where you would change the velocity is when jumping in a first person shooter（第一人称射击，按下起跳后会有一个向上的速度）, because you want an immediate change in velocity.

在这里我们实际上修改的是每次创造一个物体时赋予该物体的初速度

注意，它是一个空间属性