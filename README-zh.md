# local-ehentai

Local E-Hentai Gallery Searcher

# 功能

- 多Tag检索, 可选包含匹配或精确匹配
- 本地缩略图缓存
- 导出搜索结果为 csv / json
- 根据是否被删除/最低评分过滤
- 基于文件名/URL的本地文件过滤 & 自动匹配

# 编译

## 依赖

- Go >= 1.12

## 编译

编译包 `cmd/local-ehentai`:

```bash
go build ./cmd/local-ehentai
```

运行时将workdir设置为`web`

# 使用方法

## 启动服务

1. 下载 Sachia Lanlus 提供的 gdata.json : [Mega](https://mega.nz/#F!oh1U0SIA!WBUcf3PaOvrfIF238fnbTg) 
2. 下载并解压 [Releases](https://github.com/firefoxchan/local-ehentai/releases) 中的 local-ehentai.win.zip
3. 将 gdata.json 放到 local-ehentai.exe 同级目录
4. 运行 local-ehentai.exe
5. 访问 [http://127.0.0.1:8080](http://127.0.0.1:8080/)

## 搜索

### 语法  

一组逗号分隔的tag:value

`tag1:exact value1$, tag2:like value2 [, tag3:value3, value4, ...]`

tag留空时会搜索所有tag, value以$结尾时会精确匹配

### Tag列表

- `category`
- `uploader`
- `parody`
- `character`
- `artist`
- `group`
- `female`
- `male`
- `language`
- `misc`
- `gid` (精确匹配)

### 样例 

`artist:toyo$, female: swim`  
会匹配  
`artist`是`toyo` 并且 `female`中包含`swim`的数据

## 本地文件筛选器

### 基于文件名

#### 自动匹配

1. 把下好的压缩包放到与 local-ehentai.exe 同一文件夹下的 `files` 文件夹内, 也可以在里面创建子文件夹
2. 重启 local-ehentai.exe

#### 手动关联文件

1. 编辑与 local-ehentai.exe 同一文件夹下的 `filesMap.txt`
2. 语法: `文件名/gid`, 例: `abcd.zip/1234`
3. 重启 local-ehentai.exe

### 基于URL

1. 编辑与 local-ehentai.exe 同一文件夹下的 `existUrls.txt`
2. 重启 local-ehentai.exe

## 启用本地缩略图缓存

如果你从 [这里](https://sukebei.nyaa.si/view/2770267) 下载了缩略图包, 可以直接开启本地缩略图缓存, 不用访问eght.org

1. 解压 thumbs_raw.7z, 重命名文件夹为 thumbs
2. 把 thumbs 文件夹放到与 local-ehentai.exe 同级目录下, 然后重启 local-ehentai.exe

# 预览

![Galleries](/assets/galleries_demo_v0.0.6.png)
