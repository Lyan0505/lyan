## 数组的方法：
### js 数组其实一个对象，我们对数组进行复制是传了一个引用，针对结果是引用还是copy，原数组是否改变 分为：必写方法，只读方法：
#### 必写方法：
   * 一些会造成数组本身发生改变的方法：
   
     * splice Array.prototype.splice(start: number, deleteCount: number, ...items: any[]): any[]
        >splice 和slice 不一样，splice 改变原来的数组，slice 不会改变原来的数组，返回副本

     * arr.fill(value, start, end) 是将 arr[start, end) 的部分都填充成同一个 value。
     
        > 返回填充之后的结果 改变原来的数组；

     * push ,unshift,pop ,shift

        >因为从结果上说，unshift(1, 2)与先后调用 unshift(1), unshift(2)不同。可以推测，unshift与push是splice的特殊情况。unshift(…items) 与 splice(0, 0, …items) 是一致的，push(…items) 与 splice(this.length, 0, …items) 是一致的。BTW，shift() 与 splice(0, 1) 一致； pop()与splice(this.length - 1, 1) 一致；添加返回 数组的长度；删除 则返回删除项；
     * Array.prototype.sort(sortFn: (a: any, b: any) => number): this
     * reverse 将数组反转；

#### 只读方法：
   * forEach 与 for
   * map 映射 准确的说是满射，一一对应，返回与原来数组长度一致的新数组；
   * 聚合 reduce, reduceRight, every, some, join, indexOf, lastIndexOf, find, findIndex
       >将数组何为一个值：
   * 聚合reduce 和reduceRight
       > reduce 是遍历的同时 将某个值 试图不断更新的方法；可以非常简单地做到从一个数组中得出一个值 的操作，如求和，求最值等。
       > arr.reduce((pre,cur)=>Math.min(pre,cur))
    * 谓词 every &some
      * 全称谓词every ：是否数组中的元素全部都满足某条件
      * 存在谓词 some ：是否数组中的元素有一个满足某条件
      * 串行 join ：join 可以将一个数组以特定的分隔符转化为字符串
         > Array.prototype.toString() 可以等效于 Array.prototype.join()。当然，这两个函数对象本身是不同的。
      * 搜索 find findIndex indexOf lastIndexOf
        * 返回从头开始第一个符合条件的元素 find
        * 返回从头开始第一个符合条件的元素的索引号 findIndex
        * 返回从头开始第一个特定元素的索引号 indexOf
        * 返回从尾开始第一个特定元素的索引号 lastIndexOf
        >   [1, 3, 2, 1].find(v => v > 1); // 3
            [1, 3, 2, 1].find(v => v > 3); // undefined
        > Array.prototype.indexOf = function(item, start){
            return this.findIndex((v, i) => i >= start && v == item);
        }
       * 子数组 与 filter, slice  筛选：生成数组的保序子数组。
       * 超数组 concat 生成原数组，保持原数组在超数组的顺序不变；

#### 1.includes：
  * arr.includes(searchElement, fromIndex)
  * 一直以为只有一个参数，第二个参数可选，重该索引值查找前面的ele
  * fromIndex大于数组长度的时候 就返回false
  * includes 应用：

  ```
   var a=[2,3,4,7,9,33,322,3,4,444,3];
   var b=[3,2,7,4,6,12,3,9];
    
    //差集
    var c=a.concat(b);
    var dd=c.filter(v => !a.includes(v) || !b.includes(v) )

    console.log([...new Set(dd)])

    //数组去重 合并
    function combine(){ 
        let arr = [].concat.apply([], arguments);  //没有去重复的新数组 
        return Array.from(new Set(arr));
        } 

        var m = [1, 2, 2], n = [2,3,3]; 
        console.log(combine(m,n));  

        //其实我不是很明白上面的写
        var concatArr=m.concat(n);
        console.log(Array.from(new Set(arr)));
        //或者
        console.log([...new Set(arr)]);

  ```

  * 原来不太清楚new Set 数组去重为啥要和Arrary.from()结合使用，，原来也是转为数组的,从一个类似数组或可迭代对象中创建一个新的数组实例。
#### Arrary.from()
  * Array.from(arrayLike, mapFn, thisArg)
  * 返回一个数组实例
  * Array.from({length:10000},(v,i)=>{return i})  创建了一个数组长度为10000的数组，将伪类 数转化为数组；
  * 看到创建数组的方法，分析批量操作数组，，性能上的比较
  [http://www.jb51.net/article/109100.htm](http://www.jb51.net/article/109100.htm)
#### 搜索
* 搜索 find, findIndex, indexOf, lastIndexOf
* 返回从头开始第一个符合条件的元素 find
* 返回从头开始第一个符合条件的元素的索引号 findIndex
* 返回从头开始第一个特定元素的索引号 indexOf
* 返回从尾开始第一个特定元素的索引号 lastIndexOf

#### 
* 注意：every与some具有逻辑运算的短路性。 
* 在遍历的途中：

* every只要收到一个false，就会停止遍历；
* some只要收到一个true，就会停止遍历；



### String 常用的方法：
    
 #### str.chartAt(index)  返回子字符串
 #### str.charCodeAt(index) 返回字符串unicode 编码
 #### 静态方法：String.fromCharCode(num1,num2...)
 #### str.split() str.replace(rgExp/substr,replaceText)   str.match(正则)


  
#### [数组原型上的方法分](https://blog.csdn.net/zccz14/article/details/51582718)
   
   * [https://blog.csdn.net/zccz14/article/details/51582718](https://blog.csdn.net/zccz14/article/details/51582718)

