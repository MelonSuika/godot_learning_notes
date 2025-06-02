# 导入环节
[官方文档链接](https://docs.godotengine.org/en/stable/getting_started/workflow/importing_assets.html)
## 1. 导入资源
要在Godot中导入资源，需要将资源（图片、场景、音频、字体等等）直接放入工程文件夹中。有两种方式可以导入资源：
- 对于任意的资源类型：用系统自带的文件管理器手动拷贝。
- 有部分Godot可导入的文件类型：直接从系统的文件管理器拖拽到Godot编辑器的`文件系统`窗口（Dock Window）中。此操作只适用于资源文件类型（即Godot能够导入的文件类型）。

Godot会在内部自动导入这些文件，并将导入的资源隐藏在`res://.godot/imported`文件夹中。

当你通过代码访问已导入的资源时，需要使用资源加载器`Resource Loader`，它会处理内部文件的实际存储位置。  
![filesystem_dock](/notes/images/filesystem_dock.png)
![hidden_imported](/notes/images/hidden_imported.png)

若你尝试使用`FileAccess`类访问已导入的资源，该方法在编辑器中可能有效，但在导出的工程中会失效。

## 2. 变更导入参数
>导入参数仅存在于Godot非原生资源类型中。
这意味着，Godot自身的场景、资源文件格式（.tscn、.scn、.tres、.res）没有可在导入窗口选择的导入项。

要更改资源的导入参数，在`文件系统`窗口中选中相关资源：  
![change_parameters](/notes/images/change_parameters.png)  
在调整参数后，点击 `重新导入（Reimport）` 。要注意的是，若你在点击重新导入前选了文件系统窗口的其他文件，变更将会被丢弃。在点击重新导入后，所选参数将仅用于该资源及其未来的重新导入。

要同时变更多个资源的参数也是可以的。在文件系统窗口中将它们都选中（多选需要是同样格式的资源，比如JPG和PNG格式不同就不行），当重新导入时，所设参数将作用于所有选中的资源。