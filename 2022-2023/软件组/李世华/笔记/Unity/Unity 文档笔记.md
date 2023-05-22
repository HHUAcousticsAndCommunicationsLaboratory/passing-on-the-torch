# Unity 文档笔记

*前言：此笔记本不是给正常人看的，只是为了锻炼我自己的英语看的*

### 前言

为什么要用英文笔记？很简单，因为英语是一定要学的，而且躲不掉的

不要再后退了，直面英语。直面你害怕恐惧又不愿意面对的东西吧

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

1. **Building a structure out of a single Prefab by replicating it multiple times in different positions, for example in a grid(网格) or circle formation**