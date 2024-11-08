* .cmake 文件的作用
1. **模块化**: 允许开发者将常用的或复杂的构建逻辑抽象化，编写成模块，从而使得`CMakeLists.txt`文件更加简洁明了。
2. **复用代码**: 通过将常见配置，如查找库、编译选项等，封装到 `.cmake` 文件中，可在多个项目间共享这些构建逻辑。
3. **定制化构建过程**: 对于需要定制化构建步骤的项目，使用 `.cmake` 文件可以增加额外的构建规则和依赖管理。
4. **跨平台兼容性**: `.cmake` 可以帮助处理不同平台间的差异，例如不同的编译器选项或特定平台上可用的库，从而提升项目的跨平台兼容性。


* include函数主要用于包含其他CMake脚本文件，以便复用代码和宏定义。

* option函数
用于定义编译选项，这些选项可以控制编译过程和源代码中的条件编译。
  option(<variable> "<help_text>" [value])
  variable：定义选项的名称。
  help_text：说明选项的含义。
  value：定义选项的默认状态，通常是ON或OFF，其他值都被认为是OFF。


* string函数主要用于处理字符串，包括字符串的拼接、查找、替换等操作。
  string(LENGTH string length)：计算字符串的长度。
  string(SUBSTRING string start length result_var)：从字符串中提取子串。
  string(FIND string substring result_var)：查找子串在字符串中的位置。
  string(REPLACE old_text new_text result_var)：替换字符串中的文本。
  string(APPEND variable value)：将值追加到变量中。
  string(STRIP variable result_var)：去除变量值前后的空白字符。


* file函数主要用于执行与文件和目录相关的操作，包括文件读取、写入、复制、移动、删除等
读取文件‌：
file(READ <filename> <variable>)：将文件内容读取到变量中。
file(STRINGS <filename> <variable> [<options> ...])：读取文件内容为一串ASCII字符串到变量中，忽略二进制文件和回车符。

‌写入文件‌：
file(WRITE <filename> <content>)：将内容写入文件。
file(APPEND <filename> <content>)：向文件追加内容。
file(TOUCH <filename>)：创建空文件。

‌复制、移动和删除文件‌：
file(COPY <source> <destination>)：复制文件。
file(RENAME <source> <destination>)：重命名文件。
file(REMOVE <filename>)：删除文件。

‌目录操作‌：
file(MAKE_DIRECTORY <directory>)：创建目录。
file(REMOVE_DIRECTORY <directory>)：删除目录。
* 
* cmake_policy作用
解决CMake版本之间的兼容性问题
主要用于解决CMake版本之间的兼容性问题，确保项目在不同版本的CMake中构建时行为一致
cmake_policy(SET CMP0077 NEW)，可以防止子项目中的option()命令覆盖父项目中的变量设置，从而更好地控制子项目的配置‌
每个新发布的CMake版本都会引入一些新的策略，每个策略都有一个标识符（如CMP<NNNN>），其中<NNNN>对应四个0到9的整数。
每个策略在文档中描述了OLD和NEW的行为，以及引入的原因。通过显式或隐式设置这些策略，可以确保项目在不同版本的CMake中构建时行为一致‌

*WIN32是一个预定义的目标平台标识符，用于指定编译目标为Windows 32位环境。

* set_property用法
set_property命令用于设置全局属性，使得在多个目录或多个目标上应用相同的属性设置。
set_property(TARGET target_name PROPERTY property_name value)
TARGET：指定要设置属性的目标（如可执行文件、库等）。
PROPERTY：指定要设置的属性名称。
VALUE：属性的值。

* CMakeLists.txt文件可以使用if等语句
在CMakeLists.txt中，可以使用if、elseif、else和endif关键字来构造条件语句。
条件表达式可以使用比较操作符（EQUAL、LESS等）、逻辑操作符（AND、OR、NOT、DEFINED）和正则表达式。

* CMakeLists.txt文件的作用？
它是CMake构建系统的核心配置文件。CMakeLists.txt文件描述了项目的结构和构建过程，告诉CMake如何生成构建系统，从而自动化地编译和链接项目。


