
The file is copy from the following github https://github.com/CoreyMSchafer/code_snippets/tree/master/Python-Files.

# File Objects

## The Basics:
```
f = open("test.txt", "r")
f = open("test.txt", "w")
f = open("test.txt", "a")
f = open("test.txt", "r+")
print(f.name)
print(f.mode)
f.close()
```

## Reading Files:
It is a best practce to open file using a **CONTEXT MANAGER** so you don't need explicitly use `close()`.  
```python
with open("test.txt", "r") as f:
  pass  # do not do anything
  
  # --- Small Files
  f_contents = f.read()
  print(f_contents)
  
  # --- Big Files
  f_contents = f.readlines()
  print(f_contents)
  
  # --- With the extra lines
  f_contents = f.readline()
  print(f_contents)
  f_contents = f.readline()
  print(f_contents)
  
	# --- Without the extra lines:
  f_contents = f.readline()
  print(f_contents, end = '')
  f_contents = f.readline()
  print(f_contents, end = '')

	# --- Iterating through the file:
  for line in f:
    print(line, end = '')

	###Going Back....:
	#f_contents = f.read()
	#print(f_contents, end = '')

	###Printing by characters:
	#f_contents = f.read(100)
	#print(f_contents, end = '')
	#f_contents = f.read(100)
	#print(f_contents, end = '')
	#f_contents = f.read(100)
	#print(f_contents, end = '')

	###Iterating through small chunks:
	#size_to_read = 100
	#f_contents = f.read(size_to_read)
	#while len(f_contents) > 0:
		#print(f_contents)
		#f_contents = f.read(size_to_read)

	###Iterating through small chunks, with 10 characters:
	#size_to_read = 10
	#f_contents = f.read(size_to_read)
	#print(f_contents, end = '')
	#f.seek(0)
	#f_contents = f.read(size_to_read)
	#print(f_contents, end = '')
	#print(f.tell())
	#while len(f_contents) > 0:
		#print(f_contents, end = '*')
		#f_contents = f.read(size_to_read)
#print(f.mode)
#print(f.closed)
#print(f.read())
```
## Writing Files:

```python
# --- Writing Starts:
#with open("test2.txt", "w") as f:
	#pass
	#f.write("Test")
	#f.seek(0)
	#f.write("Test")
	#f.seek("R")

# --- Copying Files:
#with open("test.txt", "r") as rf:
	#with open("test_copy.txt", "w") as wf:
		#for line in rf:
			#wf.write(line)

# --- Copying the/your image:
###The Error
#with open("bronx.jpg", "r") as rf:
	#with open("bronx_copy.jpg", "w") as wf:
		#for line in rf:
			#wf.write(line)

# --- Copying the image starts, without chunks:
#with open("bronx.jpg", "rb") as rf:
	#with open("bronx_copy.jpg", "wb") as wf:
		#for line in rf:
			#wf.write(line)

# --- Copying the image with chunks:
#with open("bronx.jpg", "rb") as rf:
	#with open("bronx_copy.jpg", "wb") as wf:
		#chunk_size = 4096
        #rf_chunk = rf.read(chunk_size)
        #while len(rf_chunk) > 0:
            #wf.write(rf_chunk)
            #rf_chunk = rf.read(chunk_size)
 ```
