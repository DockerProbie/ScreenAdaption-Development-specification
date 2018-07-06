# ScreenAdaption
纯代码创建视图自动缩放的类，只需要赋值frame的时候使用可以自动根据屏幕大小自动缩放




## iOS开发规范


- 编写目的
- 适用范围
- 开发环境

## 一、命名规范

- 1.1 统一要求
- 1.2 类的命名
- 1.3 私有变量
- 1.4 property变量
- 1.5 宏命名
- 1.6 Enum
- 1.7 Delegate命名

## 二、私有方法及变量声明

- 2.1 声明位置
- 2.2 点语法
- 2.3 条件判断
- 2.4 三目运算符
- 2.5 错误处理
- 2.6 变量
- 2.7 init 和 dealloc
- 2.8 字面量
- 2.9 CGRect 函数
- 2.10 常量
- 2.11 布尔
- 2.12 单例
- 2.13 类构造方法

## 三、注释规范

- 3.1 属性注释
- 3.2 方法声明注释
- 3.3 导入

## 四、代码格式化

- 4.1 指针 * 位置
- 4.2 方法的声明和定义
- 4.3 代码缩进
- 4.4 对method进行分组
- 4.5 大括号写法
- 4.6 Block写法
<br/>  

<a name="iOS开发规范" />

## iOS开发规范
<br/>  

<a name="编写目的" />

### 编写目的  
> 制定开发规范,可以在团队内部形成统一的开发习惯,减少协作的理解成本。
> 此开发规范主要制定了以下方面的规范:

    1. 统一开发环境、代码格式、注释习惯、命名规则;
    2. 推荐常见性能优化解决方案;
    3. 规范化 SVN/GIT 提交习惯;
 <br/>  


<a name="适用范围" />
 
### 适用范围
    1. 客户端研发组，iOS 开发需要遵守此开发规范。
    2. 客户端研发组的其他平台开发人员，在 GIT 提交习惯方面可以参考此规范
<br/>

<a name="开发环境" />


### 开发环境
> Xcode 8.0及以上版本，目前最新版本为9.0
<br/>

<a name="一、命名规范" />

## 一、命名规范

<a name="1.1统一要求" />

### 1.1 统一要求
    含义清楚，尽量做到不需要注释也能了解其作用，若做不到，就加注释。
    使用全称，不适用缩写
<br/>

<a name="1.2类的命名" />

### 1.2 类的命名
    大驼峰式命名：每个单词的首字母都采用大写字母
    例子：RSHomeController

    后缀要求
    ViewController: 使用Controller做后缀
    例子: RSHomeController

    View: 使用View做后缀
    例子: JLBAlertView

    UITableCell:使用Cell做后缀
    例子: OrderListTitleCell

    Protocol: 使用Delegate或者DataSource作为后缀
    例子: UITableViewDelegate

    UI控件依次类推
<br/>

<a name="1.3私有变量" />

### 1.3 私有变量
    小驼峰式命名：第一个单词以小写字母开始，后面的单词的首字母全部大写。
    例子：firstName、lastName

    以下划线 _ 开头，第一个单词首字母小写
    例子：NSString * _myPrivateVariable

    私有变量放在 .m 文件中声明
<br/>

<a name="1.4property变量" />

### 1.4 property变量
    小驼峰式命名：

    例子：
    /**注释*/
    @property (nonatomic, copy) NSString *userName;

    注：禁止使用synthesize关键词

<br/>

<a name="1.5宏命名" />

### 1.5 宏命名
    全部大写，单词间用 下划线_ 分隔。[不带参数]
    例子: #define THIS_IS_AN_MACRO  @"THIS_IS_AN_MACRO"

    以字母 k 开头，后面遵循大驼峰命名。[不带参数]
    例子：#define kScreenHeight  ([UIScreen mainScreen].bounds.size.height)

    小驼峰命名。[带参数]
    例子：#define rgbColor(r,g,b) [UIColor colorWithRed:(r)/255.0 green:(g)/255.0 blue:(b)/255.0 alpha:1]
<br/>

<a name="1.6Enum" />

### 1.6 Enum

> Enum类型的命名与类的命名规则一致
>
> Enum中枚举内容的命名需要以该Enum类型名称开头

例子:

    typedef NS_ENUM(NSInteger, AFNetworkReachabilityStatus) {
         AFNetworkReachabilityStatusUnknown = -1,
         AFNetworkReachabilityStatusNotReachable = 0,
         AFNetworkReachabilityStatusReachableViaWWAN = 1,
         AFNetworkReachabilityStatusReachableViaWiFi = 2
         };
<br/>

位掩码
<br/>

> 当用到位掩码时，使用 NS_OPTIONS 宏。
<br/>

举例：
<br/>

    typedef NS_OPTIONS(NSUInteger, NYTAdCategory) {
       NYTAdCategoryAutos      = 1 << 0,
       NYTAdCategoryJobs       = 1 << 1,
        NYTAdCategoryRealState  = 1 << 2,
       NYTAdCategoryTechnology = 1 << 3
       };
<br/>

<a name="1.7Delegate命名" />

### 1.7 Delegate命名
- 类的实例必须为回调方法的参数之一, 如:
```
- (NSInteger)tableView:(UITableView*)tableView numberOfRowsInSection:(NSInteger)section 
```
- 回调方法的参数只有类自己的情况，方法名要符合实际含义, 如:
```
- (NSInteger)numberOfSectionsInTableView:(UITableView*)tableView
```
- 以类的名字开头(回调方法存在两个以上参数的情况)以表明此方法是属于哪个类的, 如:
```
- (UITableViewCell*)tableView:(UITableView*)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath
```
- 使用did和will通知Delegate已经发生的变化或将要发生的变化, 如:
```
-(NSIndexPath*)tableView:(UITableView*)tableView willSelectRowAtIndexPath:(NSIndexPath*)indexPath;

-(void)tableView:(UITableView*)tableView didSelectRowAtIndexPath:(NSIndexPath*)indexPath;

```

<a name="二、私有方法及变量声明" />

## 二、私有方法及变量声明

<a name="2.1声明位置" />

### 2.1 声明位置
- 在.m文件中最上方，定义空的category进行声明
例子:
```
@interface OrderListTitleFrame ()
{
    // 声明私有变量
    CGRect _titleImgFrame;
    CGRect _storeNameFrame;
    CGRect _orderStatusFrame;
    CGRect _lineFrame;

    CGFloat _cellHeight;
}

// 私有方法
- (CGFloat)cellHeight;

@end

@implementation OrderListTitleFrame

// 私有方法的实现
- (CGFloat)cellHeight
{
    //some code
} 
@end
```
<br/>

<a name="2.2点语法" />

### 2.2 点语法
> 应该始终使用 点语法 来访问或者修改属性，访问其他实例时首选括号。

推荐：

```
view.backgroundColor = [UIColor orangeColor];
[UIApplication sharedApplication].delegate;
```

反对：

```
[view setBackgroundColor:[UIColor orangeColor]];
UIApplication.sharedApplication.delegate;
```
<br/>

<a name="2.3条件判断" />

### 2.3 条件判断
> 条件判断主体部分应该始终使用大括号括住来防止出错，即使它可以不用大括号（例如它只需要一行）。这些错误包括添加第二行（代码）并希望它是 if 语句的一部分时。还有另外一种更危险的，当 if 语句里面的一行被注释掉，下一行就会在不经意间成为了这个 if 语句的一部分。此外，这种风格也更符合所有其他的条件判断，因此也更容易检查。

推荐：

```
if (!error) {
    return success;
}
```

反对：

```
if (!error)
    return success;

或者：

if (!error) return success;
```

<br/>

<a name="2.4三目运算符" />

### 2.4 三目运算符
> 三目运算符，? ，只有当它可以增加代码清晰度或整洁时才使用。单一的条件都应该优先考虑使用。多条件时通常使用 if 语句会更易懂，或者重构为实例变量。

推荐：

```
result = a > b ? x : y;
```

反对：

```
result = a > b ? x = c > d ? c : d : y;
```

<br/>

<a name="2.5错误处理" />

### 2.5 错误处理
> 当引用一个返回错误参数（error parameter）的方法时，应该针对返回值，而非错误变量。

推荐：

```
NSError *error;
if (![self trySomethingWithError:&error]) {
    // 处理错误
}
```

反对：

```
NSError *error;
[self trySomethingWithError:&error];
if (error) {
    // 处理错误
}
```
<br/>

<a name="2.6变量" />

### 2.6 变量
> 变量名应该尽可能命名为描述性的。除了 for() 循环外，其他情况都应该避免使用单字母的变量名。星号表示指针属于变量，例如：`NSString *text``不要写成 NSString* text`或者 `NSString * text`，常量除外。
>
> 尽量定义属性来代替直接使用实例变量。除了初始化方法`init`，` initWithCoder`:等，`dealloc`方法和自定义的`setters`和 `getters`内部，应避免直接访问实例变量。

推荐：

```
@interface NYTSection: NSObject

@property (nonatomic) NSString *headline;

@end
```

反对：

```
@interface NYTSection : NSObject {
    NSString *headline;
}
```
<br/>

变量限定符
<br/>

```
当涉及到在 ARC 中被引入变量限定符时，
限定符 (__strong, __weak, __unsafe_unretained, __autoreleasing) 
应该位于星号和变量名之间，如：NSString * __weak text。
```
<br/>

<a name="2.7init和dealloc" />

### 2.7 init 和 dealloc

> `dealloc`方法应该放在实现文件的最上面，并且刚好在` @synthesize`和`@dynamic`语句的后面。在任何类中，`init`都应该直接放在`dealloc`方法的下面。

`init`方法的结构应该像这样：

```
- (instancetype)init {
    self = [super init]; // 或者调用指定的初始化方法
    if (self) {
        // Custom initialization
    }

    return self;
}
```
<br/>

<a name="2.8字面量" />

### 2.8 字面量

> 每当创建 `NSString`，`NSDictionary`，` NSArray`，和 `NSNumber` 类的不可变实例时，都应该使用字面量。要注意 `nil `值不能传给`NSArray`和 `NSDictionary` 字面量，这样做会导致崩溃

推荐：

```
NSArray *names = @[@"Brian", @"Matt", @"Chris", @"Alex", @"Steve", @"Paul"];
NSDictionary *productManagers = @{@"iPhone" : @"Kate", @"iPad" : @"Kamal", @"Mobile Web" : @"Bill"};
NSNumber *shouldUseLiterals = @YES;
NSNumber *buildingZIPCode = @10018;
```

反对：

```
NSArray *names = [NSArray arrayWithObjects:@"Brian", @"Matt", @"Chris", @"Alex", @"Steve", @"Paul", nil];
NSDictionary *productManagers = [NSDictionary dictionaryWithObjectsAndKeys: @"Kate", @"iPhone", @"Kamal", @"iPad", @"Bill", @"Mobile Web", nil];
NSNumber *shouldUseLiterals = [NSNumber numberWithBool:YES];
NSNumber *buildingZIPCode = [NSNumber numberWithInteger:10018];

```
<br/>

<a name="2.9CGRect 函数" />

### 2.9 CGRect 函数
> 当访问一个` CGRect` 的`x`，` y`，` width`，` height` 时，应该使用 `CGGeometry` 函数代替直接访问结构体成员。苹果的 `CGGeometry` 参考中说到：

All functions described in this reference that take CGRect data structures as inputs implicitly standardize those rectangles before calculating their results. For this reason, your applications should avoid directly reading and writing the data stored in the CGRect data structure. Instead, use the functions described here to manipulate rectangles and to retrieve their characteristics.

所有功能描述在这个参考CGRect中隐式数据结构作为输入规范那些矩形之前计算结果。由于这个原因,您的应用程序应该避免直接阅读和写作在CGRect中存储的数据的数据结构。相反,使用这里描述的函数来操纵矩形和检索他们的特征。

推荐:

```
CGRect frame = self.view.frame;
CGFloat x = CGRectGetMinX(frame);
CGFloat y = CGRectGetMinY(frame);
CGFloat width = CGRectGetWidth(frame);
CGFloat height = CGRectGetHeight(frame);
```

反对：

```
CGRect frame = self.view.frame;
CGFloat x = frame.origin.x;
CGFloat y = frame.origin.y;
CGFloat width = frame.size.width;
CGFloat height = frame.size.height;

```
<br/>

<a name="2.10常量" />

### 2.10 常量
> 常量首选内联字符串字面量或数字，因为常量可以轻易重用并且可以快速改变而不需要查找和替换。常量应该声明为 `static` 常量而不是` #define` ，除非非常明确地要当做宏来使用。

推荐：

```
static NSString * const NYTAboutViewControllerCompanyName = @"The New York Times Company";

static const CGFloat NYTImageThumbnailHeight = 50.0;

```

反对：

```
#define CompanyName @"The New York Times Company"

#define thumbnailHeight 2
```
<br/>

<a name="2.11布尔" />

### 2.11 布尔
> 因为 `nil` 解析为`NO`，所以没有必要在条件中与它进行比较。永远不要直接和 `YES `进行比较，因为 `YES` 被定义为` 1`，而`BOOL` 可以多达` 8 `位。
> 
> 这使得整个文件有更多的一致性和更大的视觉清晰度。

推荐：

```
if (!someObject) {
}
```

反对：

```
if (someObject == nil) {
}
```
对于 `BOOL `来说, 这有两种用法:
```
if (isAwesome)
if (![someObject boolValue])
```

反对：

```
if ([someObject boolValue] == NO)
if (isAwesome == YES) // 永远别这么做
```

如果一个 `BOOL` 属性名称是一个形容词，属性可以省略 `is` 前缀，但为` get `访问器指定一个惯用的名字，例如：
```
@property (assign, getter=isEditable) BOOL editable;
```
<br/>

<a name="2.12单例" />

### 2.12 单例
> 单例对象应该使用线程安全的模式创建共享的实例。

```
+ (instancetype)sharedInstance {
    static id sharedInstance = nil;

    static dispatch_once_t onceToken;
    dispatch_once(&onceToken, ^{
        sharedInstance = [[self alloc] init];
    });

    return sharedInstance;
}
```
<br/>

<a name="2.13类构造方法" />

### 2.13 类构造方法
> 当类构造方法被使用时，它应该返回类型是`instancetype`而不是`id`。这样确保编译器正确地推断结果类型。

例子：

```
@interface Airplane  
+ (instancetype)airplaneWithType:(RWTAirplaneType)type;  
@end
```
<br/>

<a name="三、注释规范" />

## 三、注释规范
> 最好的代码是不需要注释的，尽量通过合理的命名、良好的代码把含义表达清楚，在必要的地方添加注释，注释需要与代码同步更新，如果做不到命名尽量的见名知意的话，就可以适当的添加一些注释或者mark

<a name="3.1属性注释" />

### 3.1 属性注释
例子：

```
/**学生*/
@property (nonatomic, strong) Student *student;
```
<br/>

<a name="3.2方法声明注释" />

### 3.2 方法声明注释
```
/**
 订单列表页接口

 @param psize [可选]: 每页条数
 @param page [可选]: 页数
 @param control 当前类
 @param success 成功回调
 @param failure 失败回调
 */
+ (void)getOrderListDataWithPsize:(NSInteger)psize
                             page:(NSInteger)page
                          control:(NSObject *)control
                          success:(void (^)(NSArray *dataArray))success
                          failure:(void (^)(NSError *error))failure;
```
<br/>

<a name="3.3导入" />

### 3.3 导入
> 如果有一个以上的 import 语句，就对这些语句进行分组。每个分组的注释是可选的。
> 
> 注：对于模块使用 @import 语法。

```
// Frameworks
@import QuartzCore;

// Models
#import "NYTUser.h"

// Views
#import "NYTButton.h"
#import "NYTUserView.h"
```
<br/>

<a name="四、代码格式化" />

## 四、代码格式化
> 把代码风格统一化，可以让代码更加易读，降低后续维护成本。

<a name="4.1指针*位置" />

### 4.1 指针 * 位置
- 定义一个对象时，指针 "*" 靠近变量
```
例子: NSString *userName;
```
<br/>

<a name="4.2方法的声明和定义" />

### 4.2 方法的声明和定义
- 在 - 、+ 和 返回值 之间留一个空格，方法名和第一个参数之间不留空格
例子：

```
- (id)initWithNibName:(NSString *)nibNameOrNilbundle:(NSBundle *)nibBundleOrNil
{
    // some code
}
```
<br/>

<a name="4.3代码缩进" />

### 4.3 代码缩进
- 使用 xcode 默认缩进，即 tab = 4空格
- 使用 xcode 中 re-indent 功能定期对代码格式进行整理
- 相同类型变量声明需要独行声明

 例子:
 ```
CGFloatoringX = frame.origin.x;
CGFloatoringY = frame.origin.y;
CGFloatlineWidth = frame.size.width;
```

- Method与Method之间空一行

例子:
 ```
  #pragma mark - private methods

 - (void)samplePrivateMethod
 {...}

 - (void)sampleForIf
 {...}
 ```
<br/>

<a name="4.4对method进行分组" />

### 4.4 对method进行分组
- 使用 #pragma mark - 方式对类的方法进行分组

例子:
```
#pragma mark - private methods

- (void)samplePrivateMethod
{...}

- (void)sampleForIf
{...}

- (void)sampleForWhile
{...}
 　　
- (void)sampleForSwitch
{...} 
　　
- (void)wrongExamples
{...}

#pragma mark - public methods

- (void)samplePublicMethodWithParam:(NSString*)sampleParam
{...}

#pragma mark - life cycle methods

- (id)initWithNibName:(NSString *)nibNameOrNil bundle:(NSBundle *)nibBundleOrNil
{...}

- (void)viewDidLoad
{...}

- (BOOL)shouldAutorotateToInterfaceOrientation:(UIInterfaceOrientation)interfaceOrientation
{...}

```
<br/>

<a name="4.5大括号写法" />

### 4.5 大括号写法
- 对于类的method: 左括号另起一行写(遵循苹果官方文档)

例子:

```
- (id)initWithNibName:(NSString *)nibNameOrNilbundle:(NSBundle *)nibBundleOrNil
{
　　   self = [super initWithNibName:nibNameOrNil

　　   bundle:nibBundleOrNil];

　　   if (self) {
           // Custom initialization
       }

　    return self;
}

```

- 对于其他使用场景: 左括号跟在第一行后边

例子：

```
- (void)sampleForIf
{
    BOOL someCondition = YES;
    if(someCondition) {
        // do something here
    }
}

- (void)sampleForWhile
{
    int i = 0;
    while (i < 10) {
        // do something here
        i = i + 1;
    }
}

- (void)sampleForSwitch
{
    SampleEnum testEnum = SampleEnumTwo;
    switch(testEnum) {
        caseSampleEnumUndefined:{
            // do something
            break;
        }
        caseSampleEnumOne:{
            // do something
            break;
        }
        caseSampleEnumTwo:{
            // do something
            break;
        }
        default:{
            NSLog(@"WARNING: there is an enum type not handled properly!");
            break;
        }
}

```

- 任何需要写大括号的部分，不得省略

```
- (void)wrongExamples
{
    BOOLsomeCondition = YES;
    if (someCondition)
        NSLog(@"this is wrong!!!");
    while(someCondition)
        NSLog(@"this is wrong!!!");
}

```
<br/>

<a name="4.6Block写法" />

### 4.6 Block写法

> 
> 根据block的长度，有不同的书写规则：
> 

- 较短的`block`可以写在一行内。
- 如果分行显示的话，`block`的右括号}应该和调用`block`那行代码的第一个非空字符对齐。
- `block`内的代码采用4个空格的缩进。
- 如果`block`过于庞大，应该单独声明成一个变量来使用。
- `^`和`(`之间，`^`和`{`之间都没有空格，参数列表的右括号`)`和`{`之间有一个空格。
<br/>

```
//较短的block写在一行内
[operation setCompletionBlock:^{ [self onOperationDone]; }];

//分行书写的block，内部使用4空格缩进
[operation setCompletionBlock:^{
    [self.delegate newDataAvailable];
}];

//使用C语言API调用的block遵循同样的书写规则
dispatch_async(_fileIOQueue, ^{
    NSString* path = [self sessionFilePath];
    if (path) {
      // ...
    }
});

//较长的block关键字可以缩进后在新行书写，注意block的右括号}和调用block那行代码的第一个非空字符对齐
[[SessionService sharedService]
    loadWindowWithCompletionBlock:^(SessionWindow *window) {
        if (window) {
          [self windowDidLoad:window];
        } else {
          [self errorLoadingWindow];
        }
}];

//较长的block参数列表同样可以缩进后在新行书写
[[SessionService sharedService]
    loadWindowWithCompletionBlock:
        ^(SessionWindow *window) {
            if (window) {
              [self windowDidLoad:window];
            } else {
              [self errorLoadingWindow];
            }
}];

//庞大的block应该单独定义成变量使用
void (^largeBlock)(void) = ^{
    // ...
};

[_operationQueue addOperationWithBlock:largeBlock];

//在一个调用中使用多个block，注意到他们不是像函数那样通过对齐的，而是同时进行了4个空格的缩进
[myObject doSomethingWith:arg1
    firstBlock:^(Foo *a) {
        // ...
    }
    secondBlock:^(Bar *b) {
        // ...
}];
```
