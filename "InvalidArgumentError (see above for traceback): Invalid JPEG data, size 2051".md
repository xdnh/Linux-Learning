## InvalidArgumentError (see above for traceback): Invalid JPEG data--Premature end of JPEG file
1. 问题描述
> 这个问题我之前遇到了，这些图片能读进来，但是缺失了一些格式信息，针对jpg文件来说，一般是由于文件下载不完整导致的，可以通过判断jpg文件的完整性来避开这个问题。
2. 具体措施
> 最简单的办法是判断文件最后两个字节是否是`\xff\xd9`，如果不是则表明文件不完整
```python
  def is_valid_jpg(jpg_file):
  """
  判断JPG文件下载是否完整
  """
  if jpg_file.split('.')[-1].lower() == 'jpg':
  with open(jpg_file, 'rb') as f:
    f.seek(-2, 2)              
    return f.read() == '\xff\xd9'
  else:
    return false
  ```
 或者
 ```python
  import os
  from PIL import Image

  root_path = "path/to/dir"
  for sub_path in os.listdir(root_path):
    sub_path = os.path.join(root_path, sub_path)
    for file_ in os.listdir(sub_path):
        file_ = os.path.join(sub_path, file_)
        try:
            Image.open(file_).load()
        except:
            print('ERROR: %s' % file_)
            continue
 ```
 ### **个人经验推荐下一种方法**
