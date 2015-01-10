LightCMSCkEditorBundle
======================

CkEditor bundle for LightCMS. If you prefer CkEditor as wysiwyg editor, this 
bundle will be usefull for LightCMS.


Installation
------------

First, you need to install LightCMS if you don't already have it. Take a look on
 [LightCMS bundle projet on github](https://github.com/fulgurio/LightCMSBundle).

After that, you need to install LightCMSTinyMCEBundle. It's easy :

1. Download FulgurioLightCMSCkEditorBundle and dependencies with composer
2. Enable the Bundle
3. Configure your yml files to use CkEditor as editor
4. Configure CkEditor as well

### Step 1: Download FulgurioLightCMSCkEditorBundle and dependencies with 
composer

First, edit composer.json, and add the bundle

``` json
{
    "require": {
        "fulgurio/light-cms-ckeditor-bundle" : "dev-master"
    }
}
```

After, just launch composer, it will load all dependencies

``` bash
$ ./composer update
```

### Step 2: Enable the bundle

Follow the installation of [LightCMS](https://github.com/fulgurio/LightCMSBundle), 
enable the bundle in the kernel:

``` php
<?php
// app/AppKernel.php

public function registerBundles()
{
    $bundles = array(
        // ...
        new Fulgurio\LightCMSCkEditorBundle\FulgurioLightCMSCkEditorBundle(),
    );
}
```

### Step 3: Configure your yml files

You need to configure LightCMSBundle. Add or complete the following lines into 
your config.yml file

```yaml
fulgurio_light_cms:
    wysiwyg: fulgurio_light_cms_ckeditor
```

That's all ! Clear your cache, and take a look at admin page of LightCMS. Now 
you have CkEditor installed !


### Step 4: Configure CkEditor as well
Ok, CkEditor is installed, may be you want to limit options. Just add and change
 the followed lines :

```yaml
fulgurio_light_cms_ckeditor:
    config:
        content_css:      bundles/mybundle/css/styles-tinymce.css
        plugins:          autolink,lists,spellchecker,style,layer,table,advhr,advimage,advlink,emotions,iespell,inlinepopups,media,contextmenu,paste,directionality,noneditable,visualchars,nonbreaking,xhtmlxtras,template
        theme_advanced_buttons1: bold,italic,underline,|,bullist,numlist,|,link,unlink,|,image,code,|,formatselect
        theme_advanced_buttons2: 
        theme_advanced_buttons3: 
```

If you know TinyMCE, you know that you can change the loaded plugin and the display of tools.
As you can see, you can add or remove plugins in 
```yaml
        plugins:          autolink,lists,spellchecker,style,layer,table,advhr,advimage,advlink,emotions,iespell,inlinepopups,media,contextmenu,paste,directionality,noneditable,visualchars,nonbreaking,xhtmlxtras,template
```
line and the tools in 
```yaml
        theme_advanced_buttons1: bold,italic,underline,|,bullist,numlist,|,link,unlink,|,image,code,|,formatselect
        theme_advanced_buttons2: 
        theme_advanced_buttons3: 
```

Easy !

Last config : usually, you forget to put the same style of front page into your admin. Here, you can put the same stylesheet into the editor with the line
```yaml
        content_css:      bundles/mybundle/css/styles-tinymce.css
```
where bundles/mybundle/css/styles-tinymce.css is the loaded css file by TinyMCE

If the page link are pink into your content, just put the style class into this 
file to display link with pink color.
