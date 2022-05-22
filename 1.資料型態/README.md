資料型態<br>
=======
<br>
基本資料型態可以區分為字元（Character）、整數（Integer）、浮點數（Float）<br>
因為在不同系統上，size都會有不一致的情況<br>
建議使用類似int16_t之類的來寫程式以避免跨平台的問題<br>
以下參考 [這裡](https://www.ibm.com/docs/en/ibm-mq/9.0?topic=platforms-standard-data-types-unix-linux-windows)
，並整理介紹<br>
日後在使用時請務必再次確認是否有改動<br>
另外提醒，以下資料型態皆有原版即有加unsigned的版本，size大小皆相同<br>
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
用來表示整數值，可以區分為 short、int、long 與 long long（C++ 11之後）<br>

Data type | short | int | long | long long 
--- | --- | --- | --- | ---
bytes (32-bit UNIX) | 2 | 4 | 4 | 8 
bytes (64-bit UNIX) | 2 | 4 | 8 | 8 
bytes (64-bit Windows) | 2 | 4 | 4 | 8 

Data type | int8_t | int16_t | int32_t | int64_t 
--- | --- | --- | --- | ---
bytes  | 1 | 2 | 4 | 8 

* 浮點數<br>
用來表示小數值，可以區分為 float、double 與 long double<br>

Data type | float | double | long double 
--- | --- | --- | --- 
bytes (32-bit UNIX) | 4 | 8 | 16 
bytes (64-bit UNIX) | 4 | 8 | 16 
bytes (64-bit Windows) | 4 | 8 | 8 
<br>
另外補充，size_t在 32-bit中是 4bytes, 在 64-bit中是 8bytes<br>
<br>

資料型態格式<br>
===========
以下紀錄可以儲存的範圍大小計算<br>
<br>
整數以int為例，因為是4bytes (32bit)，最前面的1個bit用來記錄正負，0算是在正的裡面<br>
所以 2^32 / 2 = 2147483648, 它的範圍是 -2147483648 ~ 2147483647
<br>
浮點數以float為例，因為是4bytes (32bit)，最前面的1個bit用來記錄正負<br>
接下來8個位數紀錄指數(exponent)，其中會是0~255，0到126實際上是代表-127到-1，127實際代表0，128~255實際代表1到128<br>
剩餘的23位數紀錄有效數字(fraction)，因為是科學記號所以最左邊一定是1(以二進位來看)，所以這個1不會儲存<br>
因此實際上真的能記錄的有效位數是24位(二進位)<br>
所以 2^128 ~ 3.4e+38，一般會說範圍是 e+38 ~ e-38<br>

<br>
