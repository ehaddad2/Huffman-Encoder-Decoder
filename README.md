# Huffman-Encoder
This program uses huffman compression to compress a user-specified file onto an encrypted file with a frequency file as the key and then gives the user the option to decode it.

Primary methods and description:

1. encode (params include the String representations of the input file, output file, and the frequency file): 

the encode method works to first take input from the user file, store it all in the array of frequencies and respective character-indices. From there, the huffman tree is built and the characters from the array are assigned respective huffman codes placed into an array. Once this happens, this array (cast to characters) is traversed and the codes are written as boolean bits to the .enc file.

2. decode (params same as encode but obviously the encrypted file is now the one being read from):

this method works to decode the encrypted file by first taking in the info from the frequency file into a frequency character array (aka rebuilding the one in the encoding method.) The decrypt method is then called below to finish the process.

3. decrypt (params include the BinaryIn input stream, a Node (more specifically from the huffman tree), and a the output file represented as a String):

Method rebuilds huffman tree to decode based on frequency array. Then takes input from 
the encrypted file to traverse tree and output characters to the decrypted file.

4. buildHuffmanTree (param is just an int array or the frequency array):

this method builds the huffman tree from the frequency info using a max priority queue so that when the merging happens to build the tree, simply need to poll() elements to combine (rather than searching for the min frequencies). More specifically, the two node elements with the lowest frequencies are combined into a new node and placed back into the p-queue until there's only one element left in the queue.

5. buildCode (params include a string array, root node, and a string object):

method works to traverse the huffman tree and recursively assign binary values for each respective character. More specifically, the first part of the method will initialize a string array of length 256 to store each respective code of each character at such position. Then, the helper method will traverse the huffman tree through children and marking 0 and 1 for left/right children respectively and once a leaf node is reached, the code is placed in the string array at that specific character's value. 

*Class also includes a nested Node class: a recursive implementation of the node used in the huffman tree.


