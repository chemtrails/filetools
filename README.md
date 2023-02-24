Handles boilerplate for file opening, json lines, csv rows etc. in one class

init parameters
```
path:Path
delimiter:str = ','
enc:str = 'utf-8'
```

**JSON lines**
```
ft = FileTools("file.jsonl")

ft.content
# {"a": 1, "b": 2}
  {"a": 2, "b": 3}

for line in ft.read_lines():
    print(line['a'])
# 1
  2

dict = {'a': 3, 'b': 4}
ft.append_line(dict)

ft.content
# {"a": 1, "b": 2}
  {"a": 2, "b": 3}
  {"a": 3, "b": 4}

ft.to_json_array()
# [{"a": 1, "b": 2}, {"a": 2, "b": 3}, {"a": 3, "b": 4}]

ft.clear() # empties file
```

**csv**
```
ft = FileTools("file.csv")

ft.content
# a,b,c
  d,e,f

for line in ft.read_lines():
    print(line[1])
# b
  e

l = ['g', 'h', 'i']
ft.append_line(l)

ft.content
# a,b,c
  d,e,f
  g,h,i

ft.clear()
```

**txt**
```
ft = FileTools("file.txt")

ft.content
# text 1
  text 2

for line in ft.read_lines():
    print(line)

# text 1
  text 2

ft.append_line("text 3")

ft.content
# text 1
  text 2
  text 3

ft.clear()
```
