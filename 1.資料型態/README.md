資料型態<br>
=======
<br>
基本資料型態可以區分為字元（Character）、整數（Integer）、浮點數（Float）<br>
因為在不同系統上，size都會有不一致的情況<br>
建議使用類似int16_t之類的來寫程式以避免跨平台的問題<br>
以下參考 [這裡](https://www.ibm.com/docs/en/ibm-mq/9.0?topic=platforms-standard-data-types-unix-linux-windows)
，並整理介紹<br>
日後在使用時請務必再次確認是否有改動<br>
<br>

* 字元<br>
char的size是1個bytes，是屬於最基礎的字元<br>
以下是一些延伸的型態，整理各自的size大小<br>

Data type | char | wchar_t | char8_t | char16_t | char32_t
--- | --- | --- | --- | --- | --- 
bytes  | 1 | 2 * | 1 | 2 | 4

注意!! wchar_t在不同系統可能會佔不同size<br>
size是 4byte (32-bit UNIX), 4byte (64-bit UNIX), 2byte (64-bit Windows)<br>

* 整數<br>
用來表示整數值，可以區分為 short、int、long 與 long long（C++ 11）<br>

Data type | short | int | long | long long 
--- | --- | --- | --- | ---
bytes  | 1 | 2 | 1 | 2 
bytes  | 1 | 2 | 1 | 2 

Data type | int8_t | int16_t | int32_t | int64_t | int8_t | int16_t | int32_t | int64_t 
--- | --- | --- | --- | --- | --- | --- | --- | ---
bytes  | 1 | 2 | 1 | 2 | 1 | 2 | 1 | 2 
bytes  | 1 | 2 | 1 | 2 | 1 | 2 | 1 | 2 

* 浮點數<br>
<br>
