# Huffman-Coding
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step1:
Get the input String.
<br>


### Step2:
Create tree nodes.
<br>

### Step3:
Main function to implement huffman coding.
<br>

### Step4:
Calculate frequency of occurrence.
<br>

### Step5:
Print the characters and its huffmancode.
<br>

 
## Program:

``` Python
string = 'G.Venkata Pavan Kumar'
class NodeTree(object):
    def __init__(self, left=None, right=None):
        self.left = left
        self.right=right
    def children(self):
        return (self.left,self.right)
    def nodes (self):
        return (self.left,self.right)
    def __str__(self):
        return '%s %s' %(self.left,self.right)
def huffman_code_tree (node, left=True, binString=''):
    if type(node) is str:
        return {node: binString}
    (l, r) = node.children()
    d = dict()
    d.update(huffman_code_tree (l, True, binString + '0'))
    d.update(huffman_code_tree (r, False, binString + '1'))
    return d
freq = {}
for c in string:
    if c in freq:
        freq[c] += 1
    else:
        freq[c] = 1
freq = sorted(freq.items(), key=lambda x: x[1], reverse=True)
nodes=freq
while len(nodes)>1:
    (key1,c1)=nodes[-1]
    (key2,c2)=nodes[-2]
    nodes = nodes[:-2]
    node = NodeTree (key1, key2)
    nodes.append((node,c1 + c2))
    nodes = sorted (nodes, key=lambda x: x[1], reverse=True)
huffmanCode=huffman_code_tree(nodes[0][0])
print(' Char | Huffman code ')
print('----------------------')
for (char, frequency) in freq:
    print('%-4r|%12s'%(char,huffmanCode[char]))
```
## Output:

### Print the characters and its huffmancode
<img width="231" alt="p1" src="https://user-images.githubusercontent.com/94827772/175056745-7364a5c8-7d21-42ca-a945-2bdd30b42f71.png">
<br>
<br>
<br>



## Result
Thus the huffman coding was implemented to compress the data using python programming.
