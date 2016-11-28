# PublishBintray 使用说明
Bintray ([传送门](https://bintray.com))

- 1.在项目根目录下build.gradle文件中配置插件

	    classpath 'com.github.dcendents:android-maven-gradle-plugin:1.4.1'
    	classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.2'
    
- 2.下载project.properties文件并放到你的library module目录下

	    #BINTRAY账户信息
    	BINTRAY_USER=(非登录用户名)
    	BINTRAY_APIKEY=(Bintray官网用户的编辑页面)
    	BINTRAY_GPG_PASSWORD=(此处可不填写)
    	BINTRAY_REPO = maven(Bintray官网创建名为maven的仓库)
    	
    	#开发者信息
    	DEVELOPER_ID=(开发者ID)
    	DEVELOPER_NAME=(开发者姓名)
    	DEVELOPER_EMAIL=(开发者邮箱)
    	
    	#项目信息
    	PROJ_GROUP=(项目分组,通常情况下如果你的包名为com.example.test，那么项目组ID就是com.example)
    	PROJ_NAME=(项目名称官网创建对应package)
    	PROJ_ARTIFACTID=(此ID与Model名字保持一致)
    	PROJ_VERSION=1.0.0(版本)
    	PROJ_WEBSITEURL=(项版本目网址)
    	PROJ_VCSURL=(版本控制地址)
    	PROJ_DESCRIPTION= this is android library(描述)
    	PROJ_PACKAGING="aar"(此处默认)
    	
    	#许可信息
    	LICENSENAME = 'The Apache Software License, Version 2.0'
    	LICENSEURL = 'http://www.apache.org/licenses/LICENSE-2.0.txt'
    	ALLLICENSES = ["Apache-2.0"]

- 3.在MODEL的build.gradle中添加此项目脚本

	    apply plugin: 'com.android.library'
    
    	android {
	    	compileSdkVersion 23
	    	buildToolsVersion "24.0.0"
	    	
	    	defaultConfig {
	    	minSdkVersion 15
	    	targetSdkVersion 23
	    	versionCode 1
	    	versionName "1.0"
    	}
    	buildTypes {
	    	release {
		    	minifyEnabled false
		    		proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
		    	}
	    	}
    	}
    	
		//添加插件
    	apply from: 'https://raw.githubusercontent.com/Spoon2014/PublishBintray/master/publishBintray.gradle'
    	
    	dependencies {
	    	compile fileTree(dir: 'libs', include: ['*.jar'])
	    	testCompile 'junit:junit:4.12'
	    	compile 'com.android.support:appcompat-v7:23.4.0'
    	}


- 4.编译项目后执行发布命令即可

