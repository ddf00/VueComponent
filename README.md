## package.json的结构与理解
	{
	  /* 指定应用的标识: name + version */
	  "name": "vue-component",
	  "version": "1.0.0",
	
	  /* 指定用于对应用进行编译打包, 运行, 测试等命令:  npm run xxx */
	  "scripts": {
	    "build": "webpack",
	    "dev": "webpack-dev-server"
	  },
	
	  /* 
	  指定/声明当前项目的依赖包
		对项目进行打包时需要的包 ==> devDependencies
			webpack
			babel
		项目运行得到效果需要的包 ==> dependencies
			jquery
			vue
		如果依赖包声明在了一个不准确的位置, 其实不影响下载和打包运行效果
		依赖声明使用时候会被用到
			在打包时或在运行时, 并不使用声明本身, 而是去node_modules查找并加载需要包
			在仓库中下载得到项目代码, 是没有node_modules的, 必须通过依赖声明去下载所有的包
		如果有依赖下载后没有生成对应的依赖声明, 有什么问题?
			npm install下载所有依赖包运行项目, 会抛出缺少某个包的错误 
					==> 在接手一个新的项目时有可能会碰到
	  */
	  /* 运行时依赖 */
	  "dependencies": {
		"jquery": "1.12.0",
		"vue": "2.5.0"
	  },
	
	  /* 开发/打包时依赖 */
	  "devDependencies": {
		"webpack": "4.12.1"
		"babel": "7.0.0"
	  }
	}

## 需要下载的包及作用
	webpack: 提供打包功能的包
	webpack-cli: 提供webpack命令的包
    html-webpack-plugin: 打包处理HTML(就是将打包生成的js/css在html中自动引入)
	webpack-dev-server: 
			webpack开发服务: 只在内存中打包项目生成内存中的打包文件, 并启动服务器运行
		    实现live-reload: 一旦改变了项目源码, 它就会自动重新编译打包, 并刷新浏览器
	babel-loader: 让webpack理解babel需要的对应的loader
	babel/core: babel编译ES6语法的核心包
	babel/preset-env: 包含多个解析特定ES6语法的babel插件的集合(大)包
	css-loader: 将css打包成js
	style-loader: 将js中的css代码处理到页面的<style>中
	file-loader@4.3.0: 能打包图片/字体文件/音频文件/视频文件
	url-loader@2.3.0: 可以对小于指定的图片进行base64处理(图片转换为字符串, 显示时还是显示为图片==> 减少http请求)

## babel的预设(preset)包与bebel的插件(plugin)包
	a.babel本身不编译ES6的语法
	b.babel需要基于它的plugin来做ES语法的编译
	c.每个语法都一个对应的babel plugin来编译对应的语法
	d.一个babel preset包是包含多个常用的babel plugin的集合包
	e.好处: 便于管理, 简化配置
