# Dcat Admin Extension

##### 此扩展为大合一扩展，以后使用vue3构建的组件都将合并在一起

### 演示地址
[demo: http://dcat.weiwait.cn (admin:admin)](http://dcat.weiwait.cn/admin/demo-settings 'user: admin psw: admin')

### 依赖扩展
[overtrue/laravel-filesystem-cos](https://github.com/overtrue/laravel-filesystem-cos)

[overtrue/laravel-filesystem-qiniu](https://github.com/overtrue/laravel-filesystem-qiniu)

[iiDestiny/laravel-filesystem-oss](https://github.com/iiDestiny/laravel-filesystem-oss)

### 通过 composer 安装扩展
```shell
  composer require weiwait/dcat-vue
```

### 文件系统-通过选项卡使用
```php
    public function index(Content $content): Content
    {
        $tab = Tab::make();
        $tab->add('文件存储', new \Weiwait\DcatVue\Forms\FilesystemConfig());

        return $content->title('配置')
            ->body($tab->withCard());
    }
```

[//]: # (### 文件系统-通过一级菜单使用)

[//]: # ()
[//]: # (![]&#40;https://github.com/weiwait/images/blob/main/dcat-smtp-menu.png?raw=true&#41;)

### 示例图片

![示例图片](https://raw.githubusercontent.com/weiwait/images/main/dcat-filesystem-config.png)

### 已有表单组件(采用的是Naive UI)
```php
    $form->vFile('file') // 关联文件系统配置-直传
        ->accept('mime types');
        
    $form->vMutipleFile('files') // 关联文件系统配置-直传
        ->accept('mime types');
        
    $form->vImage('image') // 关联文件系统配置-直传-裁剪
        ->ratio(16 / 9) // 固定裁剪比例
        ->large() // 放大裁剪框
        ->resolution(1920, 1080) // 重置图片分辨率
        ->jpeg(0.8) // 裁剪为jpeg格式, 参数为图片质量0-1
        ->accept('mime types');
        
    $form->vMultipleImage('images') // 关联文件系统配置-直传-裁剪
        ->ratio(16 / 9) // 固定裁剪比例
        ->large() // 放大裁剪框
        ->resolution(1920, 1080) // 重置图片分辨率
        ->jpeg(0.8) // 裁剪为jpeg格式, 参数为图片质量0-1
        ->accept('mime types');
        
    $form->vTags('tags'); // 标签
    
    $form->vList('list')
        ->sortable() // 开启排序
        ->max(8); // 限制最大添加数量
        
    $form->vKeyValue('kvs')
        ->sortable() // 开启排序
        ->serial() // 开启固定有序索引 默认为字母A-Z
        ->keys(['一', '二', '三', '四']) // serial后自定义索引
        ->list(); // serial后只提交值，保存为一维数组(索引仅作为显示)
        
    $form->vDistpicker('region')
        ->dist('province', 'city', 'district') // 开启区划
        ->coordinate('latitude', 'longitude') // 开启坐标
        ->detail('detail') // 开启详细地址
        ->disableMap() // 关闭地图
        ->mapHeight(380) // 地图高度，默认380
        ->disableRegions([440000]) // 禁用一些区划
        ->mapZoom(11); // 地图默认缩放
        ->mapZoom(11, 'zoom') // 记录地图缩放级别

    $form->vSelect('select')
        ->options(['123', '456', 'A' => 'aaa']) // 选项
        ->concatKey('separator') // 显示键
        ->optionsFromKeyValue('kvs'); // 用于结合vKeyValue进行选项选择

    $form->vMultipleSelect('ms', '多选')
        ->options(['123', '456', 'A' => 'aaa']) // 选项
        ->concatKey('separator') // 显示键
        ->optionsFromKeyValue('kvs'); // 用于结合vKeyValue进行选项选择
```

[comment]: <> (### Donate)

[comment]: <> (![示例图片]&#40;https://github.com/weiwait/images/blob/main/donate.png?raw=true&#41;)

### Dcat-admin 扩展列表
1. [图片裁剪](https://github.com/weiwait/dcat-cropper)
2. [区划级联+坐标拾取](https://github.com/weiwait/dcat-distpicker)
3. [smtp 便捷配置](https://github.com/weiwait/dcat-smtp)
4. [sms channel 便捷配置](https://github.com/weiwait/dcat-easy-sms)
