# 标题
## 一级标题
### 二级标题
正文

要创建段落，请使用空白行将一行或多行文本进行分隔

在一行的末尾添加两个或多个空格，然后按回车键,即可创建一个换行，例如：  
此处换行，也可以用一组尖括号包围br实现，例如：<br>此处换行

要加粗文本，请在单词或短语的前后各添加两个星号(*)或下划线（_）。如需加粗一个单词或短语的中间部分用以表示强调的话，请在要加粗部分的两侧各添加两个星号,例如，**加粗**，__加粗__，为适应兼容性，建议使用星号

要用斜体显示文本，请在单词或短语前后添加一个星号或下划线。要斜体突出单词的中间部分，请在字母前后各添加一个星号，中间不要带空格。例如，*斜体*，_斜体_

要同时加粗和斜体，可用三个星号或线下划线，例如,***斜体加粗***,___斜体加粗___

添加块引用使用>,例如
>这是一个段落

块引用可以包含多个段落。为段落之间的空白行添加一个 > 符号。块引用可以嵌套。在要嵌套的段落前添加一个 >> 符号。例如：

>这是一个段落
>
>>这里嵌套了一个引用
>
>块引用可以包含多个段落, 但空行也要打上>的标记

要创建有序列表，请在每个列表项前添加数字并紧跟一个英文句点然后加一个空格。数字不必按数学顺序排列，但是列表应当以数字 1 起始。，例如:<br>
1. 第一行
2. 第二行

要创建无序列表，请在每个列表项前面添加破折号 (-)、星号 (*) 或加号 (+) 。缩进一个或多个列表项可创建嵌套列表。例如：<br>
- 第一行
- 第二行

要在保留列表连续性的同时在列表中添加另一种元素，请将该元素缩进四个空格或一个制表符，如下例所示：<br>
- 第一行
- 第二行
    >添加一行

要将单词或短语表示为代码，请将其包裹在反引号中。例如：<br>
导入一个包`<vector>`

Markdown基本语法允许您通过将行缩进四个空格或一个制表符来创建代码块。如果发现不方便，请尝试使用受保护的代码块。根据Markdown处理器或编辑器的不同，您将在代码块之前和之后的行上使用三个反引号（```）或三个波浪号（~~~）。许多Markdown处理器都支持受围栏代码块的语法突出显示。使用此功能，您可以为编写代码的任何语言添加颜色突出显示。要添加语法突出显示，请在受防护的代码块之前的反引号旁边指定一种语言。例如：

```C++
#include <vector>
#include <unordered_map>
using namespace std;

struct TreeNode {
      int val;
      TreeNode *left;
      TreeNode *right;
      TreeNode(int x) : val(x), left(NULL), right(NULL) {}
};
class Solution {
public:
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        this->preorder = preorder;
        for(int i = 0; i < inorder.size(); ++i){
            map[inorder[i]] = i;
        }
        return recur(0, 0, preorder.size() - 1);
    }
private:
    vector<int> preorder;
    unordered_map<int, int> map;
    TreeNode *recur(int root, int left, int right){
        if(left > right){
            return nullptr;
        }
        TreeNode *head = new TreeNode(preorder[root]);
        int head_pos = map[preorder[root]];
        head->left = recur(root + 1, left, head_pos - 1);
        head->right = recur(root + head_pos - left + 1, head_pos + 1, right);
        return head;
    }
};
```

要创建分隔线，请在单独一行上使用三个或多个星号 (***)、破折号 (---) 或下划线 (___) ，并且不能包含其他内容，在分隔线的前后都需要添加空行。例如：<br>
这是一个段落

---

加了分割线

链接文本放在中括号内，链接地址放在后面的括号中，链接title可选。例如：<br>
这是一个链接 [Markdown语法](https://markdown.com.cn)。<br>
使用尖括号可以很方便地把URL或者email地址变成可点击的链接。
<https://markdown.com.cn>

要添加图像，请使用感叹号 (!), 然后在方括号增加替代文本，图片链接放在圆括号里，括号里的链接后可以增加一个可选的图片标题文本。给图片增加链接，请将图像的Markdown 括在方括号中，然后将链接添加在圆括号中。

要显示原本用于格式化 Markdown 文档的字符，请在字符前面添加反斜杠字符 \ 。

要添加表，请使用三个或多个连字符（---）创建每列的标题，并使用管道（|）分隔每列。您可以选择在表的任一端添加管道。

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |

单元格宽度可以变化，如下所示。呈现的输出将看起来相同。

| Syntax | Description |
| --- | ----------- |
| Header | Title |
| Paragraph | Text |

Tip: 使用连字符和管道创建表可能很麻烦。为了加快该过程，请尝试使用[Markdown Tables Generator](https://www.tablesgenerator.com/markdown_tables)。使用图形界面构建表，然后将生成的Markdown格式的文本复制到文件中。

您可以通过在标题行中的连字符的左侧，右侧或两侧添加冒号（:），将列中的文本对齐到左侧，右侧或中心。

| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Text        | And more      |

您可以通过在单词中心放置一条水平线来删除单词。结果看起来像这样。此功能使您可以指示某些单词是一个错误，要从文档中删除。若要删除单词，请在单词前后使用两个波浪号~~。例如：<br>
~~被删除的部分~~ 后面的部分。

任务列表使您可以创建带有复选框的项目列表。在支持任务列表的Markdown应用程序中，复选框将显示在内容旁边。要创建任务列表，请在任务列表项之前添加破折号-和方括号[ ]，并在[ ]前面加上空格。要选择一个复选框，请在方括号[x]之间添加 x 。例如：<br>
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the medi








