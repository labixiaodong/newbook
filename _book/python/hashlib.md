文本转md5



数据分析师必须要遵守的一个规则就是数据保密，但在跨部门沟通的时候，难免会有数据泄露的情况，所以，对于用户的姓名、手机号、地址等敏感信息，一般需要加密传输，而最常用的算法就是md5算法。
下面举个例子，使用python把业务部门的excel信息转化为用md5加密的csv文件。

```python
def get_md5(x):
    """
    字符串转为md5
    """
    md = hashlib.md5()
    md.update(x.encode())
    md_result = md.hexdigest()
    return md_result


def to_md5(file):
    df = pd.read_excel(file)
    columns = df.columns.tolist()[0]
    df[columns] = df[columns].astype('str')
    df[columns] = df[columns].apply(get_md5)
    print(df)
    df.to_csv('to_dm5.csv', index=False, encoding='utf_8_sig')


def main():
    d = r'C:\Users\jm008682\Desktop\test_md5.xlsx'
    to_md5(d)
    print('finished')
```

