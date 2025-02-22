# Jav Utils | JAV 工具箱

## 注意事项

1. 本项目中的翻译引擎依赖于[QuickStart_Rhy](https://github.com/Rhythmicc/qs)中配置的默认翻译引擎，初次使用`qs`会自动引导配置；如果你不想使用`qs`，可以自行修改main.py中的translate函数。
2. 终端内图片预览只支持系统配合[iTerm2](https://iterm2.com/)使用。
3. **请勿在墙内宣传本项目!**

## 安装

```sh
pip3 install git+https://github.com/Rhythmicc/jav.git -U
```

PS: 如果你曾经安装过jav，那么请在`QproGlobalDir`中将相关配置移除

## 支持的子命令

| 子命令 | 调用方式                             | 描述                                         |
| ------ | ------------------------------------ | -------------------------------------------- |
| cover | `jav cover` | 遍历目录下的番号视频并为其自动下载封面 |
| info   | `jav info <番号>` | 查询番号信息+获取下载链接+保存视频信息 |
| web | `jav web <番号>` | 从浏览器查询番号信息 |
| rank | `jav rank` | 查询片商的近期榜单 |
| wish | `jav wish` | 心愿单查看 |
| update | `jav update` | 更新jav |

`info`命令保存的图像文件默认为`folder.<suffix>`，nfo文件默认为`<番号>.nfo`

初次运行`jav`会自动引导配置。

## Demo

1. [点此预览视频](https://cos.rhythmlian.cn/ImgBed/dfec21722022947a677ead76b6979d40.mp4)
2. `jav info SSIS-464`

   nfo 文件内容:

   ![](https://cos.rhythmlian.cn/ImgBed/8666a497a636036147f586dddf25d5cf.png)
3. 通过`jav rank`查看片商近期榜单，可在预览后选择将其添加至心愿单；（心愿单中的内容仅会在选择下载后提示删除）。

## 开发者

1. fork本项目。

2. 增加其他自定义刮削方式，在`site`文件夹下新建一个`<站点名>.py`，结构如下:

   ```python
     from .. import *
     
     source_name = '' # 站点名
   
   
     @cover_func_wrapper
     def _cover(designation: str):
         """
         下载多个封面
   
         :param designations: 番号列表
         :param set_covername: 设置封面图片名称
         """
         # ! 此函数返回番号的封面url即可，如果没有封面则 raise Exception("未找到封面")
   
     @info_func_wrapper
     def _info(designation: str) -> dict:
         """
         查询番号信息
   
         :param designation: 番号
         :return dict: {'img', 'imgs', 'title', 'plot', 'date'}
         """
         # ! 此函数返回 {'img': '', 'imgs': '', 'title': ''}
   ```

3. 提PR。

