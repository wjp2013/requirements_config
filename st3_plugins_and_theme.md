### About VIM mode

* [Vintageous](https://github.com/guillermooo/Vintageous) 试用了一年之后我还是放弃了这个插件，虽然更新快，但是选择一行的时候会自动选上最后的换行符
* [Sublime Text 3 (OSX) Cheat Sheet](http://www.cheatography.com/martinprins/cheat-sheets/sublime-text-3-osx/)
* [官方 Keyboard Shortcuts - OSX](http://sublime-text-unofficial-documentation.readthedocs.org/en/latest/reference/keyboard_shortcuts_osx.html)
* [Sublime Text 2 Documentation](https://www.sublimetext.com/docs/2/index.html)

### ST3 Plugins

* Vintageous
* [VintageLines](https://github.com/metaphox/) 这个 fork 的项目比官方源的更好，手动下载解压到 ```~/Library/Application\ Support/Sublime\ Text\ 3/Packages``` 即可
* CTags
* All AutoComplete
* AdvancedNewFile
* ApplySyntax
* DocBlockr
* GitGutter
* Side Bar
* PlainTasks
* [Project-Manager](https://github.com/randy3k/Project-Manager) 替换内置的 Project 管理
* DashDoc 使用快捷键 ```Ctrl + Option + h``` 在 Dash 中搜索当前选中单词
* [SublimeLinter-rubocop](https://github.com/SublimeLinter/SublimeLinter-rubocop) Ruby 语法检查器
* http://emmet.io/ 前端开发用
* [Seeing Is Believing](https://github.com/JoshCheek/sublime-text-2-seeing-is-believing)
  * 先安装 Seeing Is Believing 的 gem
  * 配置 rvm 的 sublime wrapper，例如 ```rvm wrapper ruby-2.1.2@rails4 sublime```
  * 按照 [这里](https://gist.github.com/wjp2013/ce882c9ddeba2babf984) 进行修改
* SublimeREPL (这里需要配置才能在 ST3 中运行 Ruby 具体参考我的 blog）
  * pry shoud be < 0.9.12 (在2014.11.14的实际安装中发现) 
  * 根据 gem env 修改个人的配置如下
  
```bash
$ gem env
RubyGems Environment:
  - RUBYGEMS VERSION: 2.4.2
  - RUBY VERSION: 2.1.2 (2014-05-08 patchlevel 95) [x86_64-darwin13.0]
  - INSTALLATION DIRECTORY: /Users/Victor/.rvm/gems/ruby-2.1.2@rails4
  - RUBY EXECUTABLE: /Users/Victor/.rvm/rubies/ruby-2.1.2/bin/ruby
  - EXECUTABLE DIRECTORY: /Users/Victor/.rvm/gems/ruby-2.1.2@rails4/bin
  - SPEC CACHE DIRECTORY: /Users/Victor/.gem/specs
  - SYSTEM CONFIGURATION DIRECTORY: /etc
  - RUBYGEMS PLATFORMS:
    - ruby
    - x86_64-darwin-13
  - GEM PATHS:
     - /Users/Victor/.rvm/gems/ruby-2.1.2@rails4
     - /Users/Victor/.rvm/gems/ruby-2.1.2@global
  - GEM CONFIGURATION:
     - :update_sources => true
     - :verbose => true
     - :backtrace => false
     - :bulk_threshold => 1000
  - REMOTE SOURCES:
     - https://rubygems.org/
  - SHELL PATH:
     - /Users/Victor/.rvm/gems/ruby-2.1.2@rails4/bin
     - /Users/Victor/.rvm/gems/ruby-2.1.2@global/bin
     - /Users/Victor/.rvm/rubies/ruby-2.1.2/bin
     - /usr/local/bin
     - /usr/bin
     - /bin
     - /usr/sbin
     - /sbin
     - /Users/Victor/.rvm/bin
 ```

```
# SublimeREPL.sublime-settings
{
  "default_extend_env": {
    "PATH": "{HOME}/.rvm/rubies/ruby-2.1.2/bin:{PATH}",
    "GEM_PATH": "{HOME}/.rvm/gems/ruby-2.1.2@rails4"
  }
}

```

注意我安装的 rvm 并设置 ruby-2.1.2@rails4 是默认启动的环境

### ST3 Theme and Color Theme

* Dracula Color Scheme
* Spacegray
* Tomorrow COlor Schemes
* Seti UI
* [Material](https://github.com/equinusocio/material-theme) 最近喜欢这款 Theme 了

 
### Enable key repeat in Apple Lion for Sublime Text in Vim mode

```defaults write com.sublimetext.3 ApplePressAndHoldEnabled -bool false```

参考 https://gist.github.com/kconragan/2510186

### 修改 Seti UI 的边栏颜色

让边栏在被选中的情况下，当前行颜色更亮。打开 `Packages/Seti_UI/Seti.sublime-theme` 编辑如下：

```
    // Sidebar rows || selected files bg
    {
        "class": "tree_row",
        "layer0.texture": null,
        "layer0.tint": [55, 61, 86],
        "layer0.opacity": 0
    },
```

参考的

* https://github.com/kkga/spacegray/blob/master/Spacegray.sublime-theme
* https://gist.github.com/MrDrews/5452773
* http://sublimetext.userecho.com/topic/19274-theming-of-the-sidebar/

### ApplySyntax support html.erb files as Rails HTML

```
// ApplySyntax.sublime-settings
{
    // If you want exceptions reraised so you can see them in the console, change this to true.
    "reraise_exceptions": false,

    // If you want to have a syntax applied when new files are created, set new_file_syntax to the name of the syntax to use.
    // The format is exactly the same as "name" in the rules below. For example, if you want to have a new file use
    // JavaScript syntax, set new_file_syntax to 'JavaScript'.
    "new_file_syntax": false,

    // Put your custom syntax rules here:
    "syntaxes": [
        {
            // Seems must other will make .html.erb as HTML files
            "name": "Rails/HTML (Rails)",
            "rules": [
                {"file_name": ".*\\.html\\.erb$"}
            ]
        }
    ]
}
```

参考的

* https://github.com/facelessuser/ApplySyntax/blob/master/ApplySyntax.sublime-settings

### Ctags 无法编译的问题

1. brew install ctags
2. st3 安装 ctags 插件
3. 配置 ctags 插件的选项，将 ctags 的路径指向绝对路径

```
// Place your settings in the file "User/CTags.sublime-settings", which
// overrides the settings in here.
{
    "command": "/usr/local/bin/ctags"
}
```

### 相关文章

* [Sublime Text：学习资源篇](http://www.jianshu.com/p/d1b9a64e2e37)
* [Setting up Sublime Text 3 for Rails Development](https://mattbrictson.com/sublime-text-3-recommendations)
