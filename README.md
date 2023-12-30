- 👋 Hi, I’m @SrushtiSB04
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
SrushtiSB04/SrushtiSB04 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
class Empty(Exception):
    pass
class Arraystack:
    def __init__(self):
        self.data=[]
    def push(self,element):
        self.data.append(element)
    def isEmpty(self):
        return len(self.data)==0
    def pop(self):
        if self.isEmpty():
            raise Empty("stack is empty")
        return self.data.pop()

def misMatched(raw):
    stack=Arraystack()
    j=raw.find("<")
    while j!=-1:
        k=raw.find(">",j+1)
        if k==-1:
            return False
        tag=raw[j+1:k]
        if not tag.startswith("/"):
            stack.push(tag)
        else:
            if stack.isEmpty():
                return False
           elif stack.pop()!=tag[1:]:
                return False
        j=raw.find("<",k+1)
    return stack.isEmpty()
if __name__ == "__main__":
    print(misMatched("<html><head></head><body></body></html>"))
