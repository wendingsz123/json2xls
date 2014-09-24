json2xls:根据json数据生成excel表格
==================================

[![](https://badge.fury.io/py/json2xls.png)](http://badge.fury.io/py/json2xls)
[![](https://pypip.in/d/json2xls/badge.png)](https://pypi.python.org/pypi/json2xls)

json2xls不支持多层套嵌的json数据，只可以根据一层json生成表格

**安装**

    pip install json2xls

**根据json数据生成excel**

code:

    :::python
    from json2xls import Json2Xls

    json_data = '{"name": "ashin", "age": 16, "sex": "male"}'
    Json2Xls('test.xls', json_data)

command:

    python json2xls.py test.xls '{"a":"a", "b":"b"}'
    python json2xls.py test.xls '[{"a":"a", "b":"b"},{"a":1, "b":2}]'

    # from file: json of text
    python json2xls.py test.xls "`cat data.json`"

    # from file: json of line
    python json2xls.py test.xls data2.json

excel:

    age | name | sex
    ----|------|----
    30  | John | male
    18  | Alice| female


**根据请求url返回的json生成excel**

默认请求为get，get请求参数为params={}, post请求参数为data={}

code:

    :::python
    from json2xls import Json2Xls

    url = 'http://api.bosonnlp.com/sentiment/analysis'
    Json2Xls('test.xlsx', url, method='post')

command:

    python json2xls.py test.xls http://api.map.baidu.com/telematics/v3/weather\?location\=%E4%B8%8A%E6%B5%B7\&output\=json\&ak\=640f3985a6437dad8135dae98d775a09

excel:

    status | message
    -------|--------
    403    | no token header
