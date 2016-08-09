---
title: 一些Android架构框架AS安装整理
date: 2016-07-28 10:02:46
tags: RxJava,Android
---

## 一.RxJava
#### 安装
在app目录下的build.gradle中添加

    compile 'io.reactivex:rxandroid:1.2.1'
    // Because RxAndroid releases are few and far between, it is recommended you also
    // explicitly depend on RxJava's latest version for bug fixes and new features.
    compile 'io.reactivex:rxjava:1.1.6'
RxAndroid GitHub主页:
[ReactiveX/RxAndroid](https://github.com/ReactiveX/RxAndroid)
<!-- More -->
#### 关于RxJava一些不错的文章

1.[RxJava开发精要3-向响应式世界问好](http://www.tuicool.com/articles/Erqym2N)

2.[Rxjava+数据库？来用用SqlBrite和SqlDelight吧！](http://www.jianshu.com/p/4664045fa04e)

3.[可能是东半球最全的RxJava使用场景小结](http://blog.csdn.net/theone10211024/article/details/50435325)
## 二.RetroLambda
#### 安装
1.Download jdk8.

2.Add the following to your build.gradle

    buildscript {
      repositories {
        mavenCentral()
      }

      dependencies {
        classpath 'me.tatarka:gradle-retrolambda:3.2.5'
      }
    }     

    // Required because retrolambda is on maven central
    repositories {
      mavenCentral()
    }

    apply plugin: 'com.android.application' //or apply plugin: 'java'
    apply plugin: 'me.tatarka.retrolambda'
3.build.gradle中加入retrolambda编译依赖

    buildscript {
      dependencies {
      classpath 'me.tatarka:gradle-retrolambda:3.1.0'
      }
    }
4.让AS使用Java8进行语法解析

    compileOptions {
     sourceCompatibility JavaVersion.VERSION_1_8
     targetCompatibility JavaVersion.VERSION_1_8
    }
5.Configuration

    retrolambda {
      jdk System.getenv("JAVA8_HOME")
      oldJdk System.getenv("JAVA6_HOME")
      javaVersion JavaVersion.VERSION_1_6
      jvmArgs '-arg1', '-arg2'
      defaultMethods false
      incremental true
    }
参考[android上的JAVA8：使用retrolambda](http://www.open-open.com/lib/view/open1433898197176.html)

相关的github：[orfjackal/retrolambda](https://github.com/orfjackal/retrolambda)

[evant/gradle-retrolambda](https://github.com/evant/gradle-retrolambda)
## 三.Dagger2
第一步、

    apply plugin: 'kotlin-android'             // 非必须
    apply plugin: 'kotlin-android-extensions'  // 必须！！！
为什么要加一个新的plugin呢？这个是为后面使用的kapt和provided提供支持的。gradle本身不支持这两个操作。

第二步、

    buildscript {
        ext.kotlin_version = '1.0.1-2'
        repositories {
            mavenCentral()
        }
        dependencies {
            classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
            classpath "org.jetbrains.kotlin:kotlin-android-extensions:$kotlin_version"
        }
    }
第三步、

    dependencies {
        // ...其他略...
        compile 'com.google.dagger:dagger:2.2'
        kapt 'com.google.dagger:dagger-compiler:2.2'
        provided 'javax.annotation:jsr250-api:1.0'
    }

* dagger, 我们要用的正主。
* dagger-compiler, 用来生成代码。
* java.annotation, 提供Dagger意外的注解

最后，同步Gradle
#### 相关网站
[Dagger](http://square.github.io/dagger/)

#### 关于Dagger2不错的文章
1.[Dagger2 使用初步](http://www.cnblogs.com/zhuyp1015/p/5119727.html)

2.[Dagger2使用](http://www.jianshu.com/p/c2feb21064bb)

## 四.Stetho(Android调试工具)
1.添加Gradle引用:

    compile 'com.facebook.stetho:stetho:1.1.0'
只有stetho库是必须的，想查看网络请求的话，需要使用下面的两个库之一（看你的网络库用的是okhttp还是urlconnection）

    compile 'com.facebook.stetho:stetho-okhttp:1.1.0'
或者

    compile 'com.facebook.stetho:stetho-urlconnection:1.1.0'
2.在应用Application中添加代码：

    public class MyApplication extends Application {
      public void onCreate() {
        super.onCreate();
        Stetho.initialize(
            Stetho.newInitializerBuilder(this)
                .enableDumpapp(Stetho.defaultDumperPluginsProvider(this))
                .enableWebKitInspector(Stetho.defaultInspectorModulesProvider(this))
                .build());
     }}
 3.`注意：Android 4.4 开始，默认的浏览器已经是 chrome 了，所以 webview 也是 chrome 了，这就给了 webview 远程调试的能力。我们需要在 Android 里针对 Webview 做以下设置：`

    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.KITKAT) {
        WebView.setWebContentsDebuggingEnabled(true);
    }
4.在我们运行完Android程序后，我们打开Chrome，在地址输入chrom：//inspect/

#### 参考引用文章
[facebook的Android调试工具Stetho介绍和使用注意事项](http://blog.csdn.net/xgxmwang/article/details/50311817)
