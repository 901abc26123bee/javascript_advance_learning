## 理解Node類型

理解Node類型——不應被忽視的 nodeType、nodeName、nodeValue

DOM1級定義了 Node 接口，該接口將由 DOM 中的所有節點類型實現。這個 Node 接口在 JavaScript 中是作為 Node 類型實現的；除了 IE 之外，在其他所有瀏覽器中都可以訪問到這個類型。 JavaScript 中的所有節點類型都繼承自 Node 類型，因此所有節點類型都共享著相同的基本屬性和方法。   這篇講講 Node 類型常會被忽視的三個屬性：nodeType、nodeName、nodeValue。

> nodeType 屬性 

每個節點都有一個 nodeType 屬性，用於表明節點的類型，節點類型由 Node 類型中定義12個常量表示：

> nodeName 屬性與 nodeValue 屬性

  要了解節點的具體信息，可以使用 nodeName 和 nodeValue 這兩個屬性。這兩個屬性的值完全取決於節點的類型。

一般來說：

元素節點的 nodeName 是標籤名稱（大寫）
屬性節點的 nodeName 是屬性名稱
文本節點的 nodeName 永遠是 #text
文檔節點的 nodeName 永遠是 #document

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

<div id="box">hello nodeType~</div>

<script type="text/javascript">
    var element = document.getElementById("box");
    var attr = document.getElementById("box").getAttributeNode("id");
    var text = document.getElementById("box").firstChild;

    // 每個節點都有一個 nodeType 屬性，用於表明節點的類型，節點類型由 Node 類型中定義12個常量表示：
    console.log(element.nodeType);     //1
    console.log(attr.nodeType);        //2
    console.log(text.nodeType);        //3

    // 要了解節點的具體信息，可以使用 nodeName 和 nodeValue 這兩個屬性。
    // 這兩個屬性的值完全取決於節點的類型。 
    // 一般來說： 
    //      元素節點的 nodeName 是標籤名稱（大寫） 
    //      屬性節點的 nodeName 是屬性名稱 
    //      文本節點的 nodeName 永遠是 #text 
    //      文檔節點的 nodeName 永遠是 #document
    console.log(document.nodeName)    //#document
    console.log(element.nodeName);    //DIV
    console.log(attr.nodeName);       //id
    console.log(text.nodeName);       //#text

    console.log(document.nodeValue)    //null
    console.log(element.nodeValue);    //null
    console.log(attr.nodeValue);       //box
    console.log(text.nodeValue);       //hello nodeType~

</script>
</body>
</html>
```

