
# 对webpack的理解

webpack是一个预编译模块方案，通过分析项目结构，将其打包成适合浏览器加载的模块，将所有的依赖打包成一个bundle.js，通过代码分割将其分割成单元片段，进行按需加载

entry： 入口

output： 出口

resolve： 处理模块依赖路径的解析

module：处理多种解析文件的loader

plugins： 配置依赖插件