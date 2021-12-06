
### Architecture
![image](https://i.imgur.com/nh0J1Sn.png)

### Project
##### Structure
```
.
├── images
├── main.py
├── README.md
├── Reference_paper.pdf
├── requirements.txt
└── src
    ├── lsb_stegno.py
    └── n_share.py
```

##### File description
| File          | Description                                    |
|---------------|-----------------------------------------------------------|
| lsb_stegno.py | Methods to Encode and Decode data using LSB Steganography |
| n_share.py    | Methods to Split and Compress LSB Encoded images          |

### Algorithms
##### Steganography
###### Encoding data in image
```python
# Putting modified pixels in the new image
newimg.putpixel((x, y), pixel)
if (x == w - 1):
    x = 0
    y += 1
else:
    x += 1
```

###### Decoding data from image
```python
# string of binary data
binstr = ''

for i in pixels[:8]:
    if (i % 2 == 0):
        binstr += '0'
    else:
        binstr += '1'

data += chr(int(binstr, 2))
if (pixels[-1] % 2 != 0):
    return data
```
##### Visual Cryptography
###### Generating shares
```python
# Split image based on random factor
n = int(np.random.randint(data[i, j, k] + 1))
img1[i, j, k] = n
img2[i, j, k] = data[i, j, k] - n
```

###### Compressing shares
```python
img[i, j, k] = img1[i, j, k] + img2[i, j, k]
```

##### Usage
###### Setup
Install dependencies
```
pip install -r requirements.txt
```
Run using python
```
streamlit run main.py
```

