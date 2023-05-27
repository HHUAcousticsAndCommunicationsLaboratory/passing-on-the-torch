# Unity文档语法笔记

*前言：此笔记本不是给正常人看的，只是为了锻炼我自己的英语看的*

## Vector3

> [Unity - Scripting API: Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html)

This **structure** is used throughout Unity to pass 3D **positions** and **directions** around. It also contains functions for doing common vector operations.（注意Vector不是一个类，它是一个结构，即它是值类型的数据）

> other classes can be used to manipulate vectors and points as well. For example the [Quaternion](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Quaternion.html) and the [Matrix4x4](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Matrix4x4.html) classes are useful for rotating or transforming vectors and points.

**静态属性**（都是缩写）

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230527103711042.png" alt="image-20230527103711042" style="zoom:75%;" />

注：float.PositiveInfinity是正无穷大，而float.NegativeInfinity是负无穷大

*[在这个标准中，正无穷大和负无穷大是通过一种特殊的浮点数编码方式来表示的。例如，在IEEE 754单精度浮点数（binary32）中，一个浮点数由三部分组成：符号位（1位）、指数位（8位）和尾数位（23位）。当指数位全为1且尾数位全为0时，这个浮点数表示正无穷大（如果符号位为0）或负无穷大（如果符号位为1）](https://en.wikipedia.org/wiki/IEEE_754)[1](https://en.wikipedia.org/wiki/IEEE_754)[2](https://en.wikipedia.org/wiki/Single-precision_floating-point_format)。*

**对象属性**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230527104935579.png" alt="image-20230527104935579" style="zoom:75%;" />

第一个是返回长度，magnitude有大小的意思；第二个是单位化（normalized），返回一个长度为一的该向量；第三个是平方化，返回该向量的长度的平方值

**对象方法**

<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230527105546678.png" alt="image-20230527105546678" style="zoom:75%;" />

**静态方法**（太多了，建议需要的就去网站找）

| Method                                                       | Description                                                  | HowToUse                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Angle](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.Angle.html) | Calculates the angle between vectors from and.（计算向量夹角） | **public static float Angle(Vector3 from,Vector3 to)**       |
| [ClampMagnitude](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.ClampMagnitude.html) | Returns a copy of vector with its magnitude clamped to maxLength.(返回一个向量的副本，且长度为maxLength) | **public static Vector3 ClampMagnitude(Vector3 vector, float maxLength)** |
| [Cross](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.Cross.html) | Cross Product（交叉积） of two vectors. （返回两个向量的叉乘，当然也是一个向量） | public static Vector3 Cross(Vector3 lhs,Vector3 rhs)（lhs是左，rhs是右，Cross遵循左手原则，可以根据左手进行判断）（由于返回值是一个Vector3对象，可以使用normalized单位化长度） |
| [Distance](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.Distance.html) | Returns the distance between a and b.（a和b是两个position，不是direction） | **public static float Distance(Vector3 a,Vector3 b)**        |
| [Dot](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.Dot.html) | Dot Product of two vectors.(点乘)                            | **public static float Dot(Vector3 lhs,Vector3 rhs**     (我觉得的使用场景更多是这些话)For [normalized](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3-normalized.html) vectors Dot returns 1 if they point in exactly the same direction, -1 if they point in completely opposite directions and zero if the vectors are perpendicular. |
| [Lerp](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.Lerp.html) | Linearly interpolates between two points.                    | 两个点之间的线性插值的坐标，其中t是线性参数（t在0到1）                                                                        public static [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **Lerp**([Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **a**, [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **b**, float **t**); |
| [LerpUnclamped](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.LerpUnclamped.html) | Linearly interpolates between two vectors.                   | 不限制t的范围，即t可以超过1也可以小于0                                            [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **Lerp**([Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **a**, [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **b**, float **t**); |
| [Max](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.Max.html) | Returns a vector that is made from the largest components of two vectors. | public static Vector3 Max(Vector3 lhs,Vector3 rhs)(返回一个向量，该向量的x、y、z分别取每个向量x、y、z的最大值)（如（1，2，7）与（4，5，6），结果为（4，5，7）） |
| [Min](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.Min.html) | Returns a vector that is made from the smallest components of two vectors. | public static Vector3 Min(Vector3 lhs,Vector3 rhs)(同max，只不过是取最小的) |
| [MoveTowards](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.MoveTowards.html) | Calculate a **position** between the points specified by current and target, moving no farther than the distance specified by maxDistanceDelta. | public static Vector3 MoveTowards(Vector3 current,Vector3 target, float maxDistanceDelta)(在最大移动距离的限制下，从一个目标点向着另一个目标点移动时，返回移动结果的坐标)（比如由(0,0,1)移到(0,0,2)，但是限制移动0.5，那么返回的向量结果时(0,0,0.5)） |
| [Normalize](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.Normalize.html) | Makes this vector have a magnitude of 1.                     | public static [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **Normalize**([Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **value**);(返回一个单位化的向量) |
| [OrthoNormalize](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.OrthoNormalize.html) | Makes vectors normalized and orthogonal to each other.（normal法向量，tangent切向量） | public static void **OrthoNormalize**(ref [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **normal**, ref [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **tangent**);//这个是将两个向量单位化并以normal正交化                                                                           **另一个重载：**public static void **OrthoNormalize**(ref [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **normal**, ref [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **tangent**, ref [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **binormal**);                                                                                           将三个向量标准正交化，这对建立一个自己的坐标系很有用（建议看原文档） |
| [Project](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.Project.html) | Projects a vector onto another vector.                       | 将一个向量投影到另一个向量上                                       public static [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **Project**([Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **vector**, [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **onNormal**);<img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230527170244162.png" alt="image-20230527170244162" style="zoom:33%;" /> |
| [ProjectOnPlane](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.ProjectOnPlane.html) | Projects a vector onto a plane defined by a normal orthogonal to the plane. | 用于计算一个向量在一个平面上的投影。它接受两个参数：一个是要投影的向量，另一个是定义平面的法向量(planeNormal)。函数会返回一个新的向量，表示原始向量在平面上的投影。                                                                      public static Vector3 ProjectOnPlane(Vector3 vector, Vector3 planeNormal |
| [Reflect](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.Reflect.html) | Reflects a vector off the plane defined by a normal.         | <img src="C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230527195434929.png" alt="image-20230527195434929" style="zoom:50%;" />                                                  public static [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **Reflect**([Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **inDirection**, [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **inNormal**); |
| [RotateTowards](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.RotateTowards.html) | Rotates a vector current towards target.                     | 类似于MoveTowards,只不过是现在是对向量进行操作（所有向量放到原点）                                                              public static Vector3 RotateTowards(Vector3 current, Vector target, float maxRadianaDelta, float maxMagnitudeDelta) （ maxRadianaDelta是最大旋转角，maxMagnitudeDelta是最大变化长度）如果两个向量的长度不同，那么向量得出的结果的向量长度将采取线性插值的方法进行计算                                                                     线性插值的公式为：result = current + (target - current) * t  ，`t` 的值是由 `maxRadiansDelta` 参数决定的。这个参数指定了每次旋转的最大角度。随着旋转的进行，`t` 的值将根据旋转的角度增加，直到旋转完成 |
| [Scale](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.Scale.html) | Multiplies two vectors component-wise.                       | 将两个向量的x,y,z分别相乘，得到一个新向量。比如(1,2,3)乘以(4,5,6)，结果为(4,10,18)                                               public static Vector3 Scale(Vector3 a, Vector3 b) |
| [SignedAngle](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.SignedAngle.html) | Calculates the signed angle between vectors from and to in relation to axis. | 它返回一个浮点数，表示从“from”向量旋转到“to”向量所需的角度，单位为度。它以第三个参数为轴，也就是说，如果你用左手握住旋转轴，使拇指指向轴的正方向（也就是指向屏幕外），那么其他四个手指所指的方向就是旋转方向。顺时针方向是正值                                    public static float **SignedAngle**([Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **from**, [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **to**, [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **axis**); |
| [Slerp](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.Slerp.html) | Spherically interpolates between two vectors.                | 在两个向量之间进行球形插值，其中t为0到1的浮点数                                            public static [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **Slerp**([Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **a**, [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **b**, float **t**); |
| [SlerpUnclamped](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.SlerpUnclamped.html) | Spherically interpolates between two vectors.（不限制球形插值的参数t的范围，即可以超过1或者小于0） | 不限制 `t` 的范围可以让你在使用 `Vector3.SlerpUnclamped` 方法时获得更大的灵活性，但也需要注意结果可能超出预期的范围。                                           public static [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **SlerpUnclamped**([Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **a**, [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **b**, float **t**); |
| [SmoothDamp](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.SmoothDamp.html) | Gradually changes a vector towards a desired goal over time.（这是对position进行操作的） | 1. 它可以将当前位置 `current` 平滑地移动到目标位置 `target`。它通过类似于弹簧阻尼器的函数来平滑向量，永远不会超调。最常见的用途是平滑跟随摄像机。                                2. `currentVelocity` 参数是当前速度的引用。这个值在每次调用函数时都会被修改。                                                       3. `smoothTime` 参数指定了到达目标所需的大致时间。值越小，到达目标的速度就越快。可以选择使用 `maxSpeed` 参数来限制最大速度。（ `maxSpeed`默认正无穷）                                                                    4. `deltaTime` 参数指定了自上次调用此函数以来经过的时间，默认为 `Time.deltaTime` 变量。                                                       public static [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **SmoothDamp**([Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **current**, [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **target**, ref [Vector3](https://docs.unity.cn/2021.3/Documentation/ScriptReference/Vector3.html) **currentVelocity**, float **smoothTime**, float **maxSpeed** = Mathf.Infinity, float **deltaTime** = Time.deltaTime); |



---





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

刚体的速度矢量。它表示刚体位置的变化率。

In most cases you should not modify the velocity directly, as this can result in unrealistic behaviour - use AddForce instead (不要直接改速度，会失真)

Do not set the velocity of an object every physics step, this will lead to unrealistic physics simulation. A typical usage is where you would change the velocity is when jumping in a first person shooter（第一人称射击，按下起跳后会有一个向上的速度）, because you want an immediate change in velocity.

在这里我们实际上修改的是每次创造一个物体时赋予该物体的初速度

注意，它是一个世界空间属性

> 这里解释一下什么是世界空间和本地空间
>
> 我们知道脚本依附于物体存在，即如果物体坐标为(3,3,3)，那么在这个脚本里面我设定克隆体的坐标为(2,2,2)
>
> 如果(2,2,2)是世界空间属性，那么在游戏世界中它的坐标就是(2,2,2)
>
> 如果(2,2,2)是本地空间属性，那么在游戏世界中它的坐标就是（2-3，2-3，2-3），即（-1，-1，-1）
>
> 即本地空间属性是相对于当前脚本依附物的坐标而言的

​	

讲到这个世界空间与本地空间，请再允许我插入几个函数进行讲解（*注：它们都是Transform对象的成员函数*）

> 有参数为Vector3和(float x,float y, float z)的三个重载

- **当矢量Vector表示的是坐标**（注意，返回的位置受缩放影响）

  - **InverseTransformPoint**	将位置（坐标）从**世界空间**转换到**本地空间**

    在Unity中，每个对象都有一个本地坐标系和一个世界坐标系。本地坐标系是指对象相对于其父对象或根节点的坐标系，而世界坐标系是指对象相对于场景中心的坐标系。因此，当我们需要在不同的对象之间移动或旋转对象时，需要使用本地坐标系和世界坐标系之间的转换。

    此函数返回一个Vector变量。

    ```C#
    // Calculate the transform's position relative to the camera.
    using UnityEngine;
    using System.Collections;
    
    public class ExampleClass : MonoBehaviour
    {
        public Transform cam;
        public Vector3 cameraRelative;
    
        void Start()
        {
            cam = Camera.main.transform;
            Vector3 cameraRelative = cam.InverseTransformPoint(transform.position);
    
            if (cameraRelative.z > 0)
                print("The object is in front of the camera");
            else
                print("The object is behind the camera");
        }
    }//
    ```

    所有的 Transform 对象都有一个名为 InverseTransformPoint 的成员函数。这个函数用来将世界坐标系中的一个点转换为相对于该 Transform 对象所在坐标系的位置。

  - **TransformPoint** 将位置从**本地空间**转为**世界空间**

    `TransformPoint` 函数用来将一个点从物体的局部坐标系转换到世界坐标系。它的作用与 `InverseTransformPoint` 函数相反。例如，如果你有一个点在物体的局部坐标系中的位置为 `(1, 0, 0)`，你可以使用 `TransformPoint` 函数将这个点转换到世界坐标系中。

    如果一个点没有相对于另一个物体的局部坐标系的位置，那么它就只有一个世界坐标系中的位置。在这种情况下，使用 `TransformPoint` 函数将不会对这个点产生任何影响，因为这个点已经在世界坐标系中了

    ```c#
    using UnityEngine;
    using System.Collections;
    
    public class ExampleClass : MonoBehaviour
    {
        public GameObject someObject;
        public Vector3 thePosition;
    
        void Start()
        {
            // Instantiate an object to the right of the current object
            thePosition = transform.TransformPoint(Vector3.right * 2);
            Instantiate(someObject, thePosition, someObject.transform.rotation);
        }
    }
    ```

    *这两个函数的工作原理是通过矩阵运算来实现的。当你调用这两个函数时，Unity 会根据物体的位置、旋转和缩放计算出一个变换矩阵，然后使用这个矩阵来转换点的位置。这个过程涉及到一些线性代数的知识*

   

- 当矢量Vector表示的是方向的时候（该操作不受变换的缩放或位置的影响， 返回的矢量与 `direction` 的长度相同。）

  同样的，这些都是Transform对象的成员函数（不是Transform的静态函数）

  - TransformDirection 将方向Direction从**本地空间**转为**世界空间**

  - InverseTransformDirection 将方向Direction从**世界空间**转为**本地空间**

    ```c#
    using UnityEngine;
    
    public class Example : MonoBehaviour
    {
        void Start()
        {
            // transform the world forward into local space:
            Vector3 relative;
            relative = transform.InverseTransformDirection(Vector3.forward);
            Debug.Log(relative);
        }
    ```

