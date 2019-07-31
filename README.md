# 使用 PermissionsDispatcher 框架申请权限

1. 添加依赖   

在项目工程下的build.gradle文件中加入对maven仓库依赖引入的支持   
```
allprojects {
    repositories {
        jcenter()
        mavenCentral()
    }
}
```
  之后在app目录下的build.gradle文件中添加两项依赖：
```
implementation 'com.github.hotchemi:permissionsdispatcher:2.3.1'
annotationProcessor 'com.github.hotchemi:permissionsdispatcher-processor:2.3.1'
```
2. 使用注释   

以下为注解说明（注：带注释的方法一定不能private，一定要为public）：   
@RuntimePermissions：在Activity的Class声明此注解，来处理我们的权限   
@NeedsPermission:请求的权限成功后执行的方法   
@OnShowRationale:在申请权限前解释为什么需要这些权限   
@OnPermissionDenied：当用户拒绝授权时将调用该方法   
@OnNeverAskAgain：当用户选择了 “不再提醒” 将调用该方法   
其中前两个是必须使用的，也可以用Plugins中的PermissionsDispatcher插件自动生成。   

3. 调用方法   

类名：类名+PermissionsDispatcher    
方法名：@NeedsPermission注解的方法名+WithCheck
