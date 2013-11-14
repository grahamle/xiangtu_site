---
title: client文件夹
layout: page
category: organization
date: 2013-11-06
modifiedOn: 2013-11-14
---

## client文件夹

	client                                  	-- 所有客户端应用的代码
		.tmp                          			-- 临时文件夹
			scripts								-- 临时js
		app 									-- 所有的业务逻辑存放
			components 							-- 类库依赖
				angular 						-- 
				angular-cookies					-- 暂时未用
				angular-hammer					-- 触控相关库
				angular-mocks					-- 暂时未用	
				angular-resource				-- 暂时未用
				angular-sanitize				-- 暂时未用
				angular-scenario				-- 暂时未用
				angular-ui-router				-- 嵌套路由
				fastclick						-- 后面可能会去掉，消除点击延迟的库
				font-awesome					-- 符号字体
				jquery 							-- 
				jquery-ui 						-- 
				jquery.scrollTo  				-- 滚动到指定位置的jQuery插件
				pouchdb-nightly 				-- 操作本地indexed db 的库
			Documents							-- 存放电子书资源（HTML文件）
				72a5bc15-...					-- 随机码代表第一层（也是书的id）
					assets						-- 所有单元用到的多媒体资源
					unit1						-- 第一单元按card存放的HTML文件
					...							-- 别的单元文件
					package.json 				-- 关于书本信息的存档
					vocabulary.json 			-- 整本书词汇表的存档
			mock 								-- 虚拟的后台数据
				notifications.json 				-- 通知系统虚拟数据
				userData.json 					-- 用户信息虚拟数据j
				homeworkData.json 				-- 作业系统虚拟数据
			script 								-- 所有业务逻辑的实现代码
				controllers 					-- 控制器
					reader						-- 教材相关的ctrl
						reader.js 				-- 阅读器ctrl
						readerCard.js 			-- cards 部分的ctrl
						readerIndex.js 			-- 封面目录页 ctrl
					shelf 						-- 书架相关的ctrl
						shelf.js 				-- 书架 ctrl
					notification.js 			-- 通知UI
					settings.js					-- 设置面板UI
				directives 						-- 指令（用于扩展模版）
					items						-- 各题型扩展的指令代码
						item.js 				-- 最基本的HTML标签扩展：指示一个单独的题
						additionalText.js 		-- 附加阅读题
						audio.js 				-- 听力题
						bankedBlankFilling.js   -- 基于单词池库填空
						blank.js 				-- 一般填空题
						breadcrumb.js 			-- 当前位置导航
						choice.js 				-- 选择题
						contenteditable.js 		-- 内容可编辑
						dragdrop.js 			-- 拖拽
						etwired.js 				-- 连线题
						imgAnchor.js 			-- 图片系列题
						imgList.js 				-- 图片列表
						pictext.js 				-- 图文混排题
						popover.js 				-- 内部使用，弹出框
						radio.js 				-- 音频
						select.js 				-- 暂时无用
						tableblank.js 			-- 表格填空题
						text.js 				-- 文章阅读
						tof.js 					-- 正误判断
						wired.js 				-- 连线老版本
						word.js 				-- 单词卡
					reader 						-- 书体内部UI部分
						card.js 				-- 二级导航卡片的UI模版
						homeworkCard.js 		-- 作业卡UI模版
						mainSwipe.js 			-- 定义左右滑动时的界面显示
					readerOut 					-- 书体外部UI部分
						// 把外围的放进来可好？

				filters 						-- 过滤器
					etsrc.js 					-- 格式化 src，将相对地址转化为资源绝对地址
					timecode.js 				-- 格式化时间，音频打点时间换算成毫秒
					timediff.js 				-- 格式化时间，将时间转换为“几分钟前”一类的描述性语言
					unitcolor.js 				-- 格式化单元信息，单元转化为模块，有点小题大做，可简化或不用filter。
				services 						-- 服务
					audio.js					-- 音频服务
					db.js 						-- 数据库相关
					flashcard.js 				-- 单词卡
					gallery.js 					-- 画廊
					setting.js 					-- 设置服务
					user.js 					-- 用户服务
					vocabularyData.js 			-- 读取单词表的服务
					wordflashcard.js 			-- 单词表老版本
				app.js 							-- 整个应用的页面路由选择及模块继承（js的入口点）
			styles 								-- 整个应用的样式控制
				font 							-- 应用中用到的字体资源
				img 							-- 应用中用到的全局图片资源
				app.styl 						-- 整个应用的所有样式代码
				book.styl 						-- 控制书本的样式代码
				common.styl 					-- 公用的样式
				main.css 						-- 通过stylus将多个.styl文件整合编译后生成的
				main.styl 						-- 对所有.styl文件进行整合
				ui.styl 						-- 控制一些框架上的ui样式
				variables.styl   				-- 存放stylus变量
			views 								-- 应用所用到的所有模版
				reader 							-- 书本内各界面模版
				shelf                       	-- 书架界面模版			
			index.html 							-- 整个应用的入口点
		
		node_modules							-- npm安装的开发环境所需要的依赖包
			grunt及grunt相关的包				-- 
			connect-modrewrite					-- connect 中间件
			matchdep							-- 批量加载 grunt task，后面可以升级一下
			nib									-- stylus扩展库
			stylus 								-- css预处理
			swig								-- 模板库

		tools									-- 插件式工具
			book
				templates						-- 模版
					vocabulary-part.swig.html   -- 分部分单词模板
					vocabulary.swig.html 		-- 全单元单词模板

		.bowerrc 								-- 存bower的读取路径
		.editorconfig							-- 开发IDE或编辑器配置规范
		.gitignore								-- 为git配置的ignore文件
		.jshintrc								-- 统一团队js编码风格

		books.json 								-- 所有教材信息
		bower.json 								-- 阐明应用的各依赖信息
		devsetting.json 						-- 目前为DB服务的信息
		package.json 							-- 项目元数据，grunt跑起来时加载各依赖包的列表信息

		Gruntfile.js 							-- 自动化工具Grunt的配置文件
		karma-e2e.conf.js 						-- karma端到端测试
		karma.conf.js 							-- 