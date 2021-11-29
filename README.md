import os,shutil     #shutil help to remove files and folder

folderpath = r"/bin/HANAFI_Hamza"
os.chdir(folderpath)       #to change the current working directory
os.listdir()  #to check how many files we have 

list_extension = []
for fl in os.listdir():
  extension = fl.split('.')[-1]      #it split the files from .
  list_extension.append(extension)   #after split it add to the list_extension set

list_extension = list(set(list_extension))    #gives set of extension for taking each extension only one time
print(list_extension)


os.chdir(folderpath)
newfolder = folderpath + '_' + 'Arrenge'

try:
  shutil.rmtree(newfolder)   # to remove folder if there are another folder in the same name
  os.makedirs(newfolder)     # to create folder
except:
  os.makedirs(newfolder)     #if there no folder in the same name then it will work

for ex in list_extension:
  print(ex,end=',')
  os.makedirs(newfolder + "/" + ex)      #creating folder based on extension
  for fl in os.listdir():
    if ex in fl:
      try:
        shutil.copy(fl,newfolder + "/" + ex)  #for remove use move()
      except:
        print('Skip')
       
print("\nTask Done!!")




