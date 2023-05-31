# Unity 文档笔记

*前言：此笔记包含英文*



---

## [Important Classes - Time - Unity 手册](https://docs.unity.cn/cn/current/Manual/TimeFrameManagement.html)

为了更好地了解Unity中的时间序列，在此概括并解释一下Unity中的时间问题

> 在Unity中，物理系统使用固定的时间步长来工作，这对于模拟的准确性和一致性非常重要。在每一帧的开始，Unity会执行尽可能多的固定更新，以便赶上当前时间。你可以在执行顺序图中查看固定更新周期期间发生了什么。
>
> 你也可以在必要时同步执行自己的代码。这通常用于执行自己的物理相关代码，例如对刚体施加力。Unity提供了`FixedUpdate`方法作为一个入口点，让你在每个固定时间步长中执行自己的代码。
>
> `fixedDeltaTime`属性控制Unity固定时间步长循环的间隔，并以秒为单位指定。例如，值为0.01表示每个固定时间步长持续一百分之一秒，因此每秒将有100个固定时间步长。
>
> 如果你的游戏或应用程序的帧率高于每秒固定时间步长的数量，则意味着每帧持续时间小于单个固定时间步长的持续时间。在这种情况下，Unity每帧执行零或一个固定物理更新。例如，如果你的固定时间步长值为0.02，则每秒将有50次固定更新。如果你的游戏或应用程序以每秒60帧的速度运行，则大约十分之一的帧不会有固定更新。
>
> 如果你的游戏或应用程序的帧率低于固定时间步长值，则意味着每帧持续时间大于单个固定时间步长。为了解决这个问题，Unity将在每一帧中执行一次或多次固定更新，以便物理模拟赶上自上一帧以来经过的时间量。例如，如果你的固定时间步长值为0.01，则每秒将有100次固定更新。如果你的应用程序以每秒25帧的速度运行，则直到每一帧都执行四次固定更新。你可能希望这样一个场景，在其中更重要的是建模更精确的物理学而不是高帧率。(概括你妈，句句都是精华，怎么概括)

可以在Unity编辑器中的Time Manager窗口中设置`fixedDeltaTime`的值。打开Time Manager窗口的方法是：在Unity编辑器中，依次点击Edit（编辑）> Project Settings（项目设置）> Time（时间），然后在Fixed Timestep（固定时间步长）字段中输入你想要的值。

你也可以在脚本中通过修改`Time.fixedDeltaTime`属性来设置`fixedDeltaTime`的值。例如，你可以在脚本的Awake或Start方法中添加以下代码来设置`fixedDeltaTime`的值为0.02秒：

```csharp
void Awake()
{
    Time.fixedDeltaTime = 0.02f;
}
```

需要注意的是，修改`fixedDeltaTime`的值会影响物理模拟的准确性和性能。一般来说，较小的`fixedDeltaTime`值会提高物理模拟的准确性，但会更吃设备；而较大的`fixedDeltaTime`值则会降低物理模拟的准确性，但可以不那么吃性能。因此，在设置`fixedDeltaTime`的值时，需要在准确性和性能之间进行权衡。

**以下流程图说明了 Unity 用于计算单个帧中时间的逻辑，以及 [time](https://docs.unity.cn/cn/current/ScriptReference/Time-time.html)、[deltaTime](https://docs.unity.cn/cn/current/ScriptReference/Time-deltaTime.html)、[fixedDeltaTime](https://docs.unity.cn/cn/current/ScriptReference/Time-fixedDeltaTime.html) 和 [maximumDeltaTime](https://docs.unity.cn/cn/current/ScriptReference/Time-maximumDeltaTime.html) 属性如何相互关联。**

![img](https://docs.unity.cn/cn/current/uploads/Main/time-flowchart.png)

be capped to 被限制

`Time.time` 表示从游戏开始到当前帧所经过的时间，而 `deltaTime` 表示两帧之间的时间差。因此，`Time.time` 可以看作是由很多个 `deltaTime` 累加而成的。每一帧，`Time.time` 的值都会增加一个 `deltaTime`，以便计算从游戏开始到当前帧所经过的总时间。

关于后面的那个fixedTime和Update还有FixedUpdate的那个流程图，是New Bing这样解释的

> 当 `fixedTime` 落后于 `Time.time` 至少一个固定时间步长时，意味着游戏中已经经过了一个固定时间步长，此时需要进行一次物理计算。因此，Unity 引擎会调用 `FixedUpdate()` 函数来进行物理计算。
>
> 在 `FixedUpdate()` 函数执行完毕后，Unity 引擎会再次检查 `fixedTime` 是否仍然落后于 `Time.time` 至少一个固定时间步长。如果是，那么就会再次执行 `FixedUpdate()` 函数，直到 `fixedTime` 不再落后于 `Time.time` 至少一个固定时间步长为止。这样做的目的是为了保证物理计算能够以固定的时间步长进行，以便保证物理模拟的准确性。
>
> 总之，当 `fixedTime` 落后于 `Time.time` 至少一个固定时间步长时，Unity 引擎会调用 `FixedUpdate()` 函数来进行物理计算，并且会不断重复这个过程，直到 `fixedTime` 不再落后于 `Time.time` 至少一个固定时间步长为止。

----

这些属性都有各自的脚本 API 文档页面，但是查看它们的描述和输出以及它们之间的关系，有助于理解它们适当的用途。

- [Time.time](https://docs.unity.cn/cn/current/ScriptReference/Time-time.html)
- [Time.unscaledTime](https://docs.unity.cn/cn/current/ScriptReference/Time-unscaledTime.html)
- [Time.deltaTime](https://docs.unity.cn/cn/current/ScriptReference/Time-deltaTime.html)
- [Time.unscaledDeltaTime](https://docs.unity.cn/cn/current/ScriptReference/Time-unscaledDeltaTime.html)
- [Time.smoothDeltaTime](https://docs.unity.cn/cn/current/ScriptReference/Time-smoothDeltaTime.html)
- [Time.timeScale](https://docs.unity.cn/cn/current/ScriptReference/Time-timeScale.html)
- [Time.maximumDeltaTime](https://docs.unity.cn/cn/current/ScriptReference/Time-maximumDeltaTime.html)

`Time.time` 表示自玩家开始游戏以来经过的时间，因此通常会持续稳定地增加。`Time.deltaTime` 表示自上一帧以来经过的时间，因此理想情况下应该保持相对恒定。

这两个值都是应用程序或游戏中经过时间的主观度量。这意味着它们考虑了您应用的任何时间缩放。例如，您可以将 `Time.timeScale` 设置为 0.1 以实现慢动作效果（表示正常播放速度的 10%）。在这种情况下，`Time.time` 的值以“真实”时间的 10% 的速率增加。经过 10 秒钟后，`Time.time` 的值将增加 1。除了在应用程序中减慢或加快时间外，**您还可以将 `Time.timeScale` 设置为零以暂停游戏，在这种情况下，仍然会调用 `Update()` 方法，但 `Time.time` 不会增加，而 `Time.deltaTime` 为零。** 

这些值(`Time.time`、`Time.timeUpdate`、`Time.time`和`Time.deltaTime`)也受到 `Time.maximumDeltaTime` 属性值的限制。这意味着这些属性报告的任何暂停或帧率变化的长度都不会超过`maximumDeltaTime`。例如，如果发生一秒钟的延迟，但 `Time.maximumDeltaTime` 设置为默认值 0.333，则 `Time.time` 只会增加 0.333，而 `Time.deltaTime` 等于 0.333，尽管实际上在现实世界中经过了更多时间。**注意，`Time.maximumDeltaTime`并不能改变帧与帧之间实际经过的时间，它只能限制`Time.deltaTime`报告的值。**

**这些属性的未缩放版本（`Time.unscaledTime` 和 `Time.unscaledDeltaTime`）忽略了这些主观变化和限制**，并在两种情况下都报告实际经过的时间。这对于任何“即使在游戏以慢动作播放时也应以固定速度响应”的内容都很有用。一个例子是 UI 交互动画。

**下表显示了一个例子**，其中 16 帧依次经过，其中一半经过一个大延迟，在单个帧上发生。这些数字说明了 Time 类属性如何报告和响应帧率的大变化。（第8帧发生大延迟）

| Frame     | unscaledTime  | time          | unscaledDeltaTime | deltaTime     | smoothDeltaTime |
| :-------- | :------------ | :------------ | :---------------- | :------------ | :-------------- |
| 1         | 0.000         | 0.000         | 0.018             | 0.018         | 0.018           |
| 2         | 0.018         | 0.018         | 0.018             | 0.018         | 0.018           |
| 3         | 0.036         | 0.036         | 0.018             | 0.018         | 0.018           |
| 4         | 0.054         | 0.054         | 0.018             | 0.018         | 0.018           |
| 5         | 0.071         | 0.071         | 0.017             | 0.017         | 0.018           |
| 6         | 0.089         | 0.089         | 0.018             | 0.018         | 0.018           |
| 7         | 0.107         | 0.107         | 0.018             | 0.018         | 0.018           |
| 8 (**a**) | 1.123 (**b**) | 0.440 (**c**) | 1.016 (**d**)     | 0.333 (**e**) | 0.081 (**f**)   |
| 9         | 1.140         | 0.457         | 0.017             | 0.017         | 0.066           |
| 10        | 1.157         | 0.474         | 0.017             | 0.017         | 0.056           |
| 11        | 1.175         | 0.492         | 0.018             | 0.018         | 0.049           |
| 12        | 1.193         | 0.510         | 0.018             | 0.018         | 0.042           |
| 13        | 1.211         | 0.528         | 0.018             | 0.018         | 0.038           |
| 14        | 1.229         | 0.546         | 0.018             | 0.018         | 0.034           |
| 15        | 1.247         | 0.564         | 0.018             | 0.018         | 0.031           |
| 16        | 1.265         | 0.582         | 0.018             | 0.018         | 0.028           |

- **在第8帧上，尽管实际经过了一秒钟的时间，但deltaTime仅报告了0.333秒。这是因为deltaTime的值被限制在maximumDeltaTime值内。**maximumDeltaTime是Unity中的一个变量，用于限制deltaTime报告的值和增加当前time的数量。当发生大于maximumDeltaTime值的帧延迟时，Unity会限制deltaTime报告的值，并增加当前time的数量。这样做的目的是避免在帧速率峰值期间发生不良副作用(unscaledDeltaTime不受主管变化和限制)

![img](https://docs.unity.cn/cn/current/uploads/Main/time-delta-unscaled.png)

- **在第8帧上，unscaledTime增加了大约一秒钟，因为已经添加了真实（未限制）的值，而time仅增加了较小的限制值。**time值并没有赶上实际经过的时间，而是表现得好像延迟只持续了maximumDeltaTime。（(unscaledTime不受主管变化和限制)）

![img](https://docs.unity.cn/cn/current/uploads/Main/time-and-unscaled.png)

- Time.smoothDeltaTime属性报告了近期deltaTime值的近似值，**所有变化都根据算法平滑处理。这是另一种避免在运动或其他基于时间的计算中出现不合意的大步长或波动的技术。特别是那些低于maximumDeltaTime设置的阈值的波动**。**平滑算法无法预测未来的变化，但它逐渐调整其报告的值**，以平滑近期经过的delta time值的变化，使平均报告时间仍然大致等于实际经过的时间。（Time.smoothDeltaTime和Time.deltaTime都不会对实际帧数造成影响。它们只是用来控制游戏世界中物体的运动和动画。）

![img](https://docs.unity.cn/cn/current/uploads/Main/time-delta-smoothed.png)

### Unity中时间变化和物理学系统

假设您正在玩一个游戏，游戏中有一个物理对象在空中运动。在正常情况下，物理引擎会在每一帧之间模拟物理对象的运动，使其看起来像是在实时运动。

现在，假设在某一帧，游戏需要执行一些重型计算，导致这一帧的处理时间超过了maximumDeltaTime。在这种情况下，物理引擎不会尝试模拟超出maximumDeltaTime的任何时间，而是暂停物理模拟，等待帧处理完成。这意味着，在这一帧之间，物理对象不会像通常那样移动。**（*假设maximumDeltaTime设置为0.1秒。如果在某一帧，帧处理需要0.2秒才能完成，那么物理引擎会检测到这一点，并模拟maximumDeltaTime的那0.1秒，然后停止模拟。*）**

一旦帧更新完成，物理就会恢复，好像自停止以来没有经过任何时间。这意味着，在下一帧之间，物理对象将继续按照正常速度移动，就好像它从未停止过一样。

这样做的目的是避免物理系统落后太远，导致需要大量步骤才能赶上当前时间。虽然这可能会导致物理对象的运动稍微减慢，但这种减慢通常不太明显，并且通常是对游戏性能的可接受折衷。

 ### Unity中的时间尺度

Unity中的时间缩放属性（Time Scale），它可以控制游戏时间相对于现实时间的流逝速度。

如果将时间缩放设置为1.0，则游戏时间与现实时间相匹配。如果将其设置为2.0，则游戏时间将以两倍于现实时间的速度流逝，而设置为0.5则会使游戏速度减半。设置为零则会使游戏时间完全停止。

请注意，时间缩放并不会减慢执行速度，而是改变了**报告给Update和FixedUpdate函数的时间步长（通过Time.deltaTime和Time.fixedDeltaTime）**。您可以使用ScriptRef:Time-timeScale属性从脚本中设置全局时间缩放值。

> The [Time](https://docs.unity.cn/cn/current/Manual/class-TimeManager.html) window has a property to let you set the time scale globally **but it’s usually more useful to set the value from a script using the [ScriptRef:Time-timeScale](https://docs.unity.cn/cn/current/ScriptReference/Time-timeScale.html) property**.

- 对于Update来说，它是每帧调用一次，**修改Time.deltaTime的值不会影响Update函数的调用**。Update函数仍然会在每一帧被调用，但是由于Time.deltaTime的值改变了，所以基于时间的计算也会受到影响。
- 但是**修改Time.fixedDeltaTime会影响FixedUpdate函数的调用**，FixedUpdate函数以固定的时间间隔被调用，这个间隔由Time.fixedDeltaTime确定。如果您更改了Time.fixedDeltaTime的值，则FixedUpdate函数调用之间的时间间隔也会相应更改。(注意：修改Time.scaleTime会影响FixedUpdate的调用，但不会影响Time.fixedDeltaTime的值)
- - Update函数不受此影响，但是Time.deltaTime会受到此影响（成正比）                                                                   
  - FixedUpdate的调用会受到它的影响，即调用频率成正比；但fixedDeltaTime不会因此受到影响
  - 根本原因在于，Time.scaleTime影响了Time.time，而FixedUpdate是根据Time.time的流逝进行调用的

### Unity中的捕获帧率（Capture Framerate）

> A special case of time management is where you want to record gameplay as a video. Since the task of saving screen images takes considerable time, the game’s normal frame rate is reduced, and the video doesn’t reflect the game’s true performance. To improve the video’s appearance, use the Capture Framerate property. The property’s default value is 0, for unrecorded gameplay. For recording. When you set the property’s value to anything other than zero, game time is slowed and the frame updates are issued at precise regular intervals. The interval between frames is equal to , so if you set the value to 5.0 then updates occur every fifth of a second. With the demands on frame rate effectively reduced, you have time in the Update function to save screenshots or take other actions:1 / Time.captureFramerate

这段话讲的是Unity中的“捕获帧率”（Capture Framerate）属性，它用于在录制游戏视频时改善视频的外观。由于保存屏幕图像需要花费相当长的时间，因此游戏的正常帧率会降低，视频无法反映游戏的真实性能。

使用“捕获帧率”属性(即`Time.captureFramerate`)可以改善视频的外观。该属性的默认值为0，表示未录制游戏。当您将该属性的值设置为非零值时，游戏时间会减慢，并且帧更新会以精确的固定间隔发出。**帧之间的间隔等于1 / Time.captureFramerate**，因此如果您将该值设置为5.0，则每五分之一秒更新一次。由于对帧率的要求有效降低，您可以在Update函数中保存屏幕截图或执行其他操作。

为了进一步了解这个捕获帧率属性(`Time.captureFramerate`)，我们问了bing，假如想让视频录制为60帧

> 如果**您希望录制的视频以60帧每秒的速度呈现，那么您应该将Time.captureFramerate设置为60**。这样，帧之间的间隔将等于1 / 60 = 0.01667秒，即每秒更新60次。
>
> 您可以在脚本中这样设置Time.captureFramerate的值：
>
> ```C#
> void Start()
> {
>     Time.captureFramerate = 60;
> }
> 
> ```
>
> 

**关于这为什么会让游戏更难玩，bing是这么说的**

> 使用Time.captureFramerate属性可能会使游戏更难玩，因为它会减慢游戏时间，并且帧更新会以精确的固定间隔发出。这意味着游戏的响应速度可能会降低，从而影响游戏的可玩性。
>
> 例如，如果您将Time.captureFramerate设置为一个较低的值，则游戏时间会减慢，帧更新间隔会增加。这可能会导致游戏画面卡顿，操作反应迟钝，从而影响游戏体验。
>
> 当然，这并不是绝对的。您可以通过尝试不同的Time.captureFramerate值来找到一个既能改善视频外观，又不会对游戏性能产生太大影响的平衡点。
>
> 希望这能帮助您理解为什么使用Time.captureFramerate属性可能会使游戏更难玩。

----



 ##   [Unity - Manual: Variables and the Inspector](https://docs.unity.cn/2021.3/Documentation/Manual/VariablesAndTheInspector.html)

- A script makes its connection with the internal workings of Unity by implementing a class which derives from the built-in class called MonoBehaviour.

- The class name and file name must be the same to enable the script component to be attached to a GameObject.

- The main things to note, however, are the two functions defined inside the class. **The Update function is the place to put code that will handle the frame update for the GameObject. This might include movement, triggering actions and responding to user input, basically anything that needs to be handled over time during gameplay.** To enable the Update function to do its work, it is often useful to be able to set up variables, read preferences and make connections with other GameObjects before any game action takes place. **The Start function will be called by Unity before gameplay begins **(ie, before the Update function is called for the first time) and is an ideal place to do any initialization.

- Note to experienced programmers: you may be surprised that **initialization of an object is not done using a constructor function(构造函数)**. This is because the construction of objects is handled by the editor and does not take place at the start of gameplay as you might expect. If you attempt to define a constructor for a script component, it will interfere（干扰） with the normal operation of Unity and can cause major problems with the project.

- Once attached, the script will start working when you press Play and run the game. You can check this by adding the following code in the Start function:（There, we learn a new method "Debug.Log(string)"）

  Debug.Log is a simple command that just prints a message to Unity’s console output. If you press Play now, you should see the message at the bottom of the main Unity editor window and in the Console window (menu: Window > General > Console).

  ```c#
  // Use this for initialization 
  void Start ()
  { 
      Debug.Log("I am alive!");
  }
  ```

- In C#, the simplest way to see a variable in the Inspector is to declare it as public. An alternative method is to use SerializeField(This is an attribute). Conversely, you can use HideInInspector to prevent a public variable from being displayed in the Inspector.

- Serialize是序列化，它是一个把数据对象转换成二进制流保存为本地文件的过程，方便将对象从一个地方移动到另一个地方，使游戏数据不容易被直接篡改

- When Unity serializes your scripts, it only serializes public fields. If you also want Unity to serialize your private fields you can add the SerializeField attribute to those fields.

  ```C#
  	[SerializeField]
      private Rigidbody rb;
  ```

- Unity serializes all your script components, reloads the new assemblies, and recreates your script components from the serialized versions. This serialization is done with an internal Unity serialization system; not with .NET's serialization functionality.

  The serialization system can do the following:

  - CAN serialize public non-static fields (of serializable types)
  - CAN serialize nonpublic non-static fields marked with the [SerializeField](https://docs.unity.cn/ScriptReference/SerializeField.html) attribute.
  - CANNOT serialize static fields.
  - CANNOT serialize properties.

- Unity can serialize fields of the following types:
  - All classes inheriting from UnityEngine.Object, for example GameObject, Component, MonoBehaviour, Texture2D, AnimationClip.
  - All basic data types, such as int, string, float, bool.
  - Some built-in types, such as Vector2, Vector3, Vector4, Quaternion, Matrix4x4, Color, Rect, LayerMask.
  - Arrays of a serializable type
  - Lists of a serializable type
  - Enums
  - Structs

-  If you put one element in a list (or array) twice, when the list gets serialized, you'll get two copies of that element, instead of one copy being in the new list twice.（实际上就是说，你会得到两份拷贝而不是一个数据的两个引用）

- If you want to serialize a custom Struct field, you must give the Struct the [System.Serializable] attribute.

- **Hint:** Unity won't serialize Dictionary, however you could store a List<> for keys and a List<> for values, and sew them up in a non serialized dictionary on Awake(). This doesn't solve the problem of when you want to modify the dictionary and have it "saved" back, but it is a handy trick in a lot of other cases.（字典不能被序列化，但你可以在脚本里面使用字典的）

- 你可以使用一些方法来绕过这个限制，比如：

  - [使用List模拟字典的键值对，在Awake或Start方法中将键值复制到字典中](https://zhuanlan.zhihu.com/p/397879702)[3](https://zhuanlan.zhihu.com/p/397879702)。
  - [使用[**SerializableDictionary**\]插件，它可以让你自定义你需要序列化的字典类型，并在Inspector窗口中显示](https://blog.csdn.net/JianZuoGuang/article/details/102536605)[4](https://blog.csdn.net/JianZuoGuang/article/details/102536605)。
  - [使用[**OdinSerializer**\]插件，它可以让你序列化任何类型的数据，并提供了更多的功能和优化](https://kuroha.vip/unity/unity_jsonutility.html)[5](https://kuroha.vip/unity/unity_jsonutility.html)。

- cnblog关于序列化的解释：

  序列化 (Serialization)是将对象的状态信息转换为可以存储或传输的形式的过程。在序列化期间，对象将其当前状态写入到临时或持久性存储区。以后，可以通过从存储区中读取或反序列化对象的状态，重新创建该对象。

  序列化使其他代码可以查看或修改，那些不序列化便无法访问的对象实例数据。

- [Unity - Scripting API: SerializeField](https://docs.unity.cn/ScriptReference/SerializeField.html)

- Serialization is the automatic process of transforming data structures or object states into a format that Unity can store and reconstruct later.(序列化的定义)
- The Inspector window does not communicate with the Unity Scripting API when it displays the values of a field. If you use properties in your script, any of the property getters and setters are never called when you view or change values in the Inspector windows as Unity serializes the Inspector window fields directly.

- When you change and save a script, Unity reloads all the currently loaded script data. It first stores all serializable variables in all loaded scripts, and after loading the scripts restores them. All data that is not serializable is lost after the script is reloaded.（注意保存和恢复是两个概念）This affects all Editor windows, as well as all MonoBehaviours in the project. Unlike other cases of serialization in Unity, private fields are serialized by default when reloading, even if they don’t have the ‘SerializeField’ attribute.

- **HideInInspector**: Makes a variable not show up in the inspector but be serialized.

  Use:

  ```c#
  using UnityEngine;
  
  public class Example : MonoBehaviour
  {
      // Make the variable p not show up in the inspector
      // but be serialized.
      [HideInInspector]
      int p = 5;
  }
  ```

  Unity - Scripting API: HideInInspector](https://docs.unity.cn/2021.3/Documentation/ScriptReference/HideInInspector.html)

- Unity will actually let you change the value of a script’s variables while the game is running. This is very useful for seeing the effects of changes directly without having to stop and restart. **When gameplay ends, the values of the variables will be reset to whatever they were before you pressed Play**. This ensures that you are free to tweak your object’s settings without fear of doing any permanent damage.

---

## [Unity - Manual: Instantiating Prefabs at run time](https://docs.unity.cn/2021.3/Documentation/Manual/InstantiatingPrefabs.html)

Compared with creating GameObjects from scratch using code, instantiating Prefabs using code has many advantages because you can:

- Instantiate a Prefab using one line of code. Creating equivalent GameObjects from scratch requires many more lines of code.
- Set up, test, and modify the Prefab quickly and easily using the **Scene**,**view, Hierarchy** and **Inspector**
- Change which Prefab is instantiated without changing the code. You can make a simple rocket into a super-charged rocket, without any code changes.

You can drag a different Prefab into the **My Prefab** field in the Inspector to change which Prefab is instantiated, without having to change the script.

Because this first example is very simple, it may not seem to provide any advantage over(超过) just placing a Prefab into the Scene yourself. However, being able to instantiate Prefabs using code provides you with powerful abilities to dynamically（动态地） create complex configurations of GameObjects while your game or app is running, as shown in the following examples.

学点英语：

replace sth with sth： In this scenario, the example script deletes and replaces the complete, operational robot Prefab with a wrecked robot Prefab. 

### Basics of instantiating a Prefab

详见请看语法笔记，这只讲一些我遇到的东西

讲一讲**Input Manager**

> [Unity - Manual: Input Manager](https://docs.unity.cn/2021.3/Documentation/Manual/class-InputManager.html)

*to access it, from Unity’s main menu, go to **Edit > Project Settings**, then select **Input Manager** from the navigation on the right.*

> The **Input Manager** uses the following types of controls:
>
> - **Key** refers to any key on a physical keyboard, such as W, Shift, or the space bar.
> - **Button** refers to any button on a physical controller (for example, gamepads), such as the X button on a remote control.
> - A **virtual axis** (plural: **axes**) is mapped to a control, such as a button or a key. When the user activates the control, the axis receives a value in the range of [–1..1]. You can use this value in your **scripts**
>   

cnm，map怎么还有映射的意思

- 概念一，Physical Keys

  > The Physical keys option allows you to map key codes to the physical keyboard layout, rather than to the language-specific layout that may vary between users in different regions.
  >
  > For example, on some keyboards the first row of letters reads “QWERTY”, and on others it reads “AZERTY”. This means if you scripted specific controls to use the well known “WASD” keys for movement, they would not be in the correct physical arrangement (like the arrow-key arrangement) on an AZERTY-layout keyboard.
  >
  > With Physical Keys enabled, Unity uses a generic ANSI/ISO “Qwerty” layout to represent the **physical location** of the keys regardless of the user’s actual layout. This means if you specify the “Q” key, it will always be the left-most letter on the first row of letter keys, even if the user’s keyboard has a different letter in that position.

​		简单来讲就是由于不同地方的键盘是不一样的，咱们就用做这个功能，不以字母来，而是以按键所在键盘位		置来

- virtual axes

  下面这个就是一些属性，没错就是edit>project settings到Input Manager的解释

  > | **Property**                                                 | **Function**                                                 |
  > | :----------------------------------------------------------- | :----------------------------------------------------------- |
  > | **Name**                                                     | Axis name. You can use this to access the axis from scripts. |
  > | **Descriptive Name, Descriptive Negative Name**（Descriptive弃用的） | These values are deprecated and do not work. Previously, they displayed for the user on the Rebind Controls screen at startup, but this screen has also been deprecated. |
  > | **Negative Button, Positive Button**（Negative反向，Positive正向） | The controls to push the axis in the negative and positive direction respectively. These can be keys on a keyboard, or buttons on a joystick or mouse. |
  > | **Alt Negative Button, Alt Positive Button**                 | Alternative controls to push the axis in the negative and positive direction respectively. |
  > | **Gravity**（重力）                                          | Speed in units per second that the axis falls toward neutral when no input is present.（用人话来说，当你不按下按钮的时候，该方向上的衰减程度；gravity最大为1000，即此时） |
  > | **Dead**                                                     | How far the user needs to move an analog stick before your application registers the movement. At runtime, input from all analog devices that falls within this range will be considered null.（指游戏手柄或其他输入设备的摇杆或轴的中心位置周围的区域。在这个区域内，输入值被认为是零，即使实际上输入设备的轴并没有完全回到中心位置。Deadzone的目的是为了减少输入设备的误差，使玩家可以更容易地控制游戏中的角色或物体。） |
  > | **Sensitivity**（灵敏度）                                    | Speed in units per second that the axis will move toward the target value. This is for digital devices only.（例如，如果Sensitivity的值为1，则输入设备的轴的完整范围将映射到游戏中的完整范围。如果Sensitivity的值为2，则输入设备的轴的完整范围将映射到游戏中的一半范围。这意味着，如果玩家将输入设备的轴移动到其完整范围的一半位置，则游戏中的角色或物体将只移动到其完整范围的四分之一位置） |
  > | **Snap**                                                     | If enabled, the axis value will reset to zero when pressing a button that corresponds to the opposite direction.（这个我解释不明白，不知道）（这是通义千问的解释：根据 Unity 的文档，当启用 InputManager 的 Snap 功能时，如果您按下了某个按钮，那么系统将会自动检测该按钮所代表的方向，并将轴心位置重置为零。这意味着，如果您按下了一个向左的按钮，那么系统将会将轴心位置重置到左侧，以便您可以通过移动屏幕来实现向左的移动。同样地，如果您按下了一个向右的按钮，那么系统将会将轴心位置重置到右侧，以便您可以通过移动屏幕来实现向右的移动。 因此，当您使用 InputManager 的 Snap 功能时，您可以通过移动屏幕来实现小球的各种移动方向和轨迹，而不仅仅是简单地让小球随机地左右移动。不过需要注意的是，在某些情况下，例如当您需要实现小球的碰撞检测或者其他一些特殊的功能时，您需要在代码中手动控制小球的位置和方向，而不是完全依赖于 InputManager 的 Snap 功能。） |
  > | **Type**                                                     | The type of input that controls the axis. Select from these values:  - Key or Mouse button - Mouse Movement - Joystick Axis |
  > | **Axis**                                                     | The axis of a connected device that controls this axis.      |
  > | **JoyNum**                                                   | The connected Joystick that controls this axis. You can select a specific joystick, or query input from all joysticks. |

(这个英语太简单了，我就不讲了)![image-20230520112425139](C:\Users\32620\AppData\Roaming\Typora\typora-user-images\image-20230520112425139.png)

---

### To illustrate the strength of instantiating Prefabs at run time, here are some basic situations where they are useful:

(为了说明在运行时实例化预制件的强大之处，这里有一些基本情况，它们非常有用)

1. **Building a structure out of a single Prefab by replicating it multiple times in different positions, for example in a grid(网格) or circle formation**