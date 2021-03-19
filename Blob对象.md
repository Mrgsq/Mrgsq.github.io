# Blob
`Blob`对象表示一个不可变、原始数据的类文件对象。它的数据可以按文本或二进制的格式进行读取，也可以转换成`ReadableStream`来用于数据操作。
# 构造函数
`Blob(blobParts[, options])`, 返回一个新创建的`Blob`对象，其内容有参数中给定的数组串联组成。
# 属性
`Blob.size`,该属性为只读属性，返回`Blob`对象中所包含数据的大小（字节）
`Blob.type`,只读属性，返回`Blob`对象中所包含数据的MIME类型。如果类型位置，则该值为空字符串。
# 方法
`Blob.slice([start[, end][, contentType]]])`, 返回一个`Blob`对象，包含了源`Blob`对象中指定范围的数据。
`Blob.stream()` 返回一个能读取`Blob`内容的`ReadableStream`。
`Blob.text()` 返回一个`Promise`对象，包含`Blob`所有内容的UTF-8格式的`USVString`
`Blob.arrayBuffer()`返回一个`Promise`对象，包含`Blob`所有内容的二进制格式的`ArrayBuffer`