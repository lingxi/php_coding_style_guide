# [灵析团队]PHP 代码风格指南

在 [fig-psr2](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md) 和 [laravel](https://laravel.com/) 的代码规范基础上，加上团队一些自己的习惯，总结出自己的一套以供交流学习。

## 基础

首先阅读[「PSR 规范」PSR-2 编码风格规范](https://laravel-china.org/topics/2079)了解基础规范。后文主要是对其的一些补充。

## `namespace` 以及 `use` 声明

- `namespace` 应该与 `<?php` 间有一行换行
- `use` 按照长度从短到长排序
- 全部命名空间的类调用 `use` 申明代替 `\`

```php
<?php

namespace App;

use App;
use App\Bar;
use App\Services\Baz;

class Foo
{
	App::run();
}
```

> 如果使用 [sublime](http://www.sublimetext.com/) 作为文本编辑器，可以使用 [PHP Companion](https://packagecontrol.io/packages/PHP%20Companion) 来引入命名空间。配置 `use_sort_length` 为 true 就可以自动为 `use` 按长度排序了。其他编辑器或者 `ide` 应该可以找到类似插件。
## 结构控制

### `if`, `elseif`, `else`, `foreach`, `while`...

所有的 `}` 后必须有一行换行，`{` 上面也应该有一行换行

```php
<?php

start();

if {true} {
	//
}

end();
```

### `!` 的使用

在 `!` 有一个空格

```php
<?php

if (! $isTrue) {
	//
}

return ! empty($data);
```

## `try`, `catch`

如果使用 `php7.1` 的话，有两个或以上异常做相同的处理，需要使用新的语法结构

```php
<?php

try {
	//
} catch (FirstException | SecondException $e) {
	//
}
```

## `PHP` 函数

非类，接口，`trait` 的函数命名使用下划线命名，且先调用 `function_exists` 查看是否已经申明

```
<?php

if (! function_exists('code_style')) {
	function code_style() {
		//
	}
}

```

## 和 `laravel` 不同的地方

### `.` 字符串连接

在 `.` 左右两边都有空格

```php
<?php

$coding = 'coding';

echo 'php ' . $coding . ' style';
```

> 供学习交流，有不同看法欢迎和我们讨论，🍻🍻🍻
