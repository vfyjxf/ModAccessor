# ModAccessor

一个简单的Gradle Plugin,用于解决编译期无法访问私有类型/字段/方法的问题。

**注意:你需要自己处理运行时的access transform**

**通常来说，你可以直接向forge/neoforge提供AT文件,它会自动应用到mod类上**

## Usage

[![ModAccessor](https://img.shields.io/maven-metadata/v/https/plugins.gradle.org/m2/dev/vfyjxf/modaccessor/dev.vfyjxf.modaccessor.gradle.plugin/maven-metadata.xml.svg?label=ModAccessor)](https://plugins.gradle.org/plugin/dev.vfyjxf.modaccessor)

```groovy

plugins{
    id("dev.vfyjxf.modaccessor") version "1.1"
}
modAccessor {
    createTransformConfiguration(configurations.compileOnly)
    accessTransformerFiles = project.files('src/main/resources/META-INF/accesstransformer.cfg')
}

dependencies {
    accessCompileOnly(("com.simibubi.create:create-${minecraft_version}:6.0.4-61:slim"))
}
```

accessConfiguration不是transitive的，所以你需要手动添加依赖。

## Credit

[fabric loom](https://github.com/FabricMC/fabric-loom) : 提供了LocalMaven的解决方案，并且源码转换基于loom的设计

[moddev gradle](https://github.com/NeoForged/ModDevGradle) : 提供了最初版本的解决思路，帮我搞清楚了Artifact Transform如何工作
