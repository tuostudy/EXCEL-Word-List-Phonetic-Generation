欢迎来到单词表单词书大全库！墨墨词库可以说我是见过覆盖范围最广最全面的词库了，1000多本单词书包含多种不同的格式有英文和中文，从全国各大教材中小学同步到大学四六级再到考研托福雅思GRE出国留学还有终极单词Wordly Wise成人本科剑桥朗文国际英语教程美国当代语料库等等，几乎可以在这里找到任何你想要的词书（鬼知道我花了多少时间来整理这么多单词书）

<div style="background-color:;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 25px;"></div>


<div style="background-color:#eb86a4;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 20px;">全套下载地址</div>


<div style="background-color:;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 25px;"></div>


### 百度网盘：https://pan.baidu.com/s/1qQfpH5Rz8dkqViDaoUerPA?pwd=6666

### 夸克网盘：https://pan.quark.cn/s/ff9ac854296f

### 阿里云盘：https://www.aliyundrive.com/s/XBRZKtrLNKr

<div style="background-color:;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 25px;"></div>


<div style="background-color:#eb86a4;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 20px;">纯英文文件夹内有无中文翻译的txt文本</div>


<div style="background-color:;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 25px;"></div>


可以拿来当做默写本自测或者导入不背单词、拓词、欧路词典app进行学习

[![LqXe10.png](https://s1.ax1x.com/2022/04/27/LqXe10.png)](https://tuostudy.com/%F0%9F%93%9C%20050%23%20%E5%8D%95%E8%AF%8D%E6%96%87%E6%9C%AC/%F0%9F%93%81%2001%23%20%E7%BA%AF%E8%8B%B1%E6%96%87%E7%89%88/)

<div style="background-color:#eb86a4;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 20px;">分单元文件夹内有含单元信息的txt文本</div>


<div style="background-color:;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 25px;"></div>


可以导入list背单词app学习

[![LqXtc6.png](https://s1.ax1x.com/2022/04/27/LqXtc6.png)](https://tuostudy.com/%F0%9F%93%9C%20050%23%20%E5%8D%95%E8%AF%8D%E6%96%87%E6%9C%AC/%F0%9F%93%81%2002%23%20%E5%88%86%E5%8D%95%E5%85%83%E7%89%88/)

<div style="background-color:#eb86a4;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 20px;">中文释义文件夹内有中文释义的excel文本（自己新增了音标，源码如下：）</div>
           
import requests
import os
from lxml import etree
from openpyxl.styles import Font
from openpyxl.styles import Alignment
from openpyxl.styles import Side, Border
from openpyxl import load_workbook


def get_phonetic():
    print('————' * 10)
    workbook = load_workbook(file)  # 导入excel表格
    worksheet = workbook['Sheet1']  # 读取excel中的sheet1这张表

    worksheet.insert_cols(idx=2, amount=2)  # 向右插入两列准备存放数据，idx:插入列的位置，amount:插入的列数
    worksheet.insert_rows(idx=0, amount=1)  # 在顶部插入一行写入注释，idx:插入行的位置，amount:插入的行数
    worksheet['A1'] = '单词'  # 如果你的单词本第一行原本就有这些注释就不用这代码了，直接删掉就行
    worksheet['B1'] = '英音'
    worksheet['C1'] = '美音'
    worksheet['D1'] = '释义'

    font = Font(name='微软雅黑', size=20, bold=False)  # 设置全局字体大小样式
    worksheet['A1'].font = font
    worksheet['B1'].font = font
    worksheet['C1'].font = font
    worksheet['D1'].font = font

    alignment = Alignment(horizontal="left")  # 设置单元格对齐方式，用于修复墨墨词库csv文件顶部两处单元格的对齐异常问题
    worksheet['A2'].alignment = alignment  # 如果不需要此代码可删除
    worksheet['D2'].alignment = alignment  # 如果不需要此代码可删除
    border = Border(Side(style=None))  # 设置单元格边框样式，用于修复墨墨词库csv文件顶部两处单元格的边框异常问题
    worksheet['A2'].border = border  # 如果不需要此代码可删除
    worksheet['D2'].border = border  # 如果不需要此代码可删除

    worksheet.column_dimensions['A'].width = 30  # 设置全局列宽
    worksheet.column_dimensions['B'].width = 30
    worksheet.column_dimensions['C'].width = 30
    worksheet.column_dimensions['D'].width = 30
    workbook.save(file)

    row_index = 2  # 默认结果放到第二行开始

    for row in worksheet.iter_rows(min_row=2, max_col=3):  # 以行迭代(最小第二行,最多第3列)
        word = row[0].value  # 获取第一列所有表格数据
        # 请确保你的单词在第1列，如果你的单词在第N列，请将代码换成：word = row[0+N].value，还要记得改其他各处代码中的数字！
        url = 'https://www.youdao.com/w/eng/{}'.format(word)  # 从有道获取音标
        try:
            data = requests.get(url).text
            html = etree.HTML(data)
            num1 = 'A' + str(row_index)
            num2 = 'B' + str(row_index)
            num3 = 'C' + str(row_index)
            num4 = 'D' + str(row_index)

            British_pron = html.xpath('//*[@id="phrsListTab"]/h2/div/span[1]/span/text()')[0]
            American_pron = html.xpath('//*[@id="phrsListTab"]/h2/div/span[2]/span/text()')[0]
            print('正在输出：' + British_pron, American_pron)

            worksheet.cell(row=row_index, column=2).value = British_pron  # 默认将英式音标的结果放到第2列
            worksheet.cell(row=row_index, column=3).value = American_pron  # 默认将美式音标的结果放到第3列

            worksheet[num1].font = font
            worksheet[num2].font = font
            worksheet[num3].font = font
            worksheet[num4].font = font
        except Exception as e:
            print(e, word)
            num1 = 'A' + str(row_index)
            num4 = 'D' + str(row_index)
            worksheet[num1].font = font
            worksheet[num4].font = font

        row_index += 1
    workbook.save(file)
    print("单词音标全部转换完毕！已经成功保存在原文件：" + file)
    print('————' * 10)


if __name__ == '__main__':
    file_list = []

    print('欢迎来到多个xlsx批量单词音标转换小程序')
    print('注意事项：\n'
          '1.请确保你的网络通畅！\n'
          '2.请确保你的文件后缀格式为xlsx而非csv!\n'
          '3.请确保你的单词全部在第一列!\n'
          '4.运行过程漫长请耐心等待，不要中途退出，否则不会得到任何结果!\n'
          '5.有什么不懂的地方，欢迎私信联系我，B站搜：TUO图欧君\n'
          )

    while True:  # 用户设置阶段
        try:
            file_folder = input('请输入你的excel文件所在目录（比如：F:\我的文件夹）：')  # 输入你的excel表格的文件存储位置
            if not os.path.exists(file_folder):  # 判断文件是否存在
                print('你输入的文件路径有误，请重新输入！')
            else:
                print('————' * 10)
                print('————文件目录匹配成功！————')
                break
        except NameError:
            print('你输入的文件路径有误，请重新输入！')

    for root, dirs, files in os.walk(file_folder):
        for file in files:
            file_name = os.path.join(file)
            if file_name.endswith(".xlsx"):
                file_path = os.path.join(root, file_name)
                file_list.append(file_path)

    print('已成功导入：')
    print(file_list)
    for i in file_list:
        file = i
        print('正在运行：' + i)
        get_phonetic()




<div style="background-color:;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 25px;"></div>


可以拿来当做默写本对答案或者制作成txt后导入ANKI记忆卡进行学习

[![LqjkDO.png](https://s1.ax1x.com/2022/04/27/LqjkDO.png)](https://tuostudy.com/%F0%9F%93%9C%20050%23%20%E5%8D%95%E8%AF%8D%E6%96%87%E6%9C%AC/%F0%9F%93%81%2003%23%20%E4%B8%AD%E6%96%87%E9%87%8A%E4%B9%89/)

<div style="background-color:#eb86a4;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 20px;">英文释义文件夹内有英文释义的excel文本</div>


<div style="background-color:;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 25px;"></div>


适合喜欢英汉双解的高阶学习者使用或者与中文释义合并制作成txt后导入ANKI记忆卡进行学习

[![LqjRR1.png](https://s1.ax1x.com/2022/04/27/LqjRR1.png)](https://tuostudy.com/%F0%9F%93%9C%20050%23%20%E5%8D%95%E8%AF%8D%E6%96%87%E6%9C%AC/%F0%9F%93%81%2004%23%20%E8%8B%B1%E6%96%87%E9%87%8A%E4%B9%89/)

<div style="background-color:#eb86a4;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 20px;">更多最新文件夹内有更多的词书与最新的词书</div>


<div style="background-color:;
            width:full;
            height:30px;
            color: black;
            text-align: center;
            font-weight: bold;
            font-size: 25px;"></div>


【考研最新词书】是专为2023考研学生单独设置的新文件夹，23考研必上岸！

【软件同步词书】文件夹则为更多软件的单词表版本，如果墨墨词库还无法满足你，那你不妨试试更多APP的词库版本~

[![LqvMFJ.png](https://s1.ax1x.com/2022/04/27/LqvMFJ.png)](https://tuostudy.com/%F0%9F%93%9C%20050%23%20%E5%8D%95%E8%AF%8D%E6%96%87%E6%9C%AC/%F0%9F%93%81%2005%23%20%E6%9B%B4%E5%A4%9A%E6%9C%80%E6%96%B0/%F0%9F%93%81%20%E8%BD%AF%E4%BB%B6%E5%90%8C%E6%AD%A5%E8%AF%8D%E4%B9%A6/)

幕布目录大纲（右上角可搜索）：https://www.mubucm.com/doc/58us-9vVDN

词书来源：知乎大佬@ourongxing，词书整理：B站UP主图欧君

[导入背单词软件创建自定义词书详细图文教程（点这里）](https://www.bilibili.com/read/cv14556183)

更多资料都整理在网盘了：

## [学习资源船舱（点这里上船）](https://tuo.icodeq.com/quark)

★上万款学习生活办公软件影视资源免费无偿分享★
