#Hasnain Mazhar
#11479845

import re

static = False

#------------------------- 10% -------------------------------------
# The operand stack: define the operand stack and its operations
opstack = []

# now define functions to push and pop values on the opstack according to your
# decision about which
# end should be the hot end. Recall that `pass` in python is a
# no-op: replace it with your code.
def opPop():
    if len(opstack) > 0:
        val = opstack.pop()
        return val
    pass

def opPush(value):
    opstack.append(value)
    pass

#-------------------------- 20% -------------------------------------
# The dictionary stack: define the dictionary stack and its operations
# now define functions to push and pop dictionaries on the dictstack, to define
# name, and to lookup a name

dictstack = []
#pop the dictionary off the dictstack
def dictPop():
    return dictstack.pop()
pass
#push the dictionary on the dictstack
def dictPush(d, link):
    dictstack.append((d, link))
    pass
#push the name and value on the dictstack
def define(name, value):
    if len(dictstack) < 1:
        d = {}
        link = 0
    else:
        (d, link) = dictPop()
    d[name] = value
    dictPush(d, link)
    pass
#pop the values and name from opstack
def psDef():
    value = opPop()
    name = opPop()
    define(name, value)
    pass

def in_dict(d, name):
    return name in d
pass

def getLink(name):
    index = 0
    dictstack.reverse()
    for(d,link) in dictstack:
        if in_dict(d, name):
            dictstack.reverse()
            return len(dictstack) - index - 1
        index += 1
    print("error: name is undefined")

pass
#return the value associated with name in dictionary
def lookup(name):
    if static:
        index = -1
        while True:
            (d,link) = dictstack[index]
            if in_dict(d, name):
                return d[name]
            else:
                if index == link:
                    print("error")
                index = link
    else:
        link = getLink(name)
        (d, link) = dictstack[link]
        return d[name]
    pass

# return the value associated with name
# what is your design decision about what to do when there is no definition
# for name

#--------------------------- 10% -------------------------------------
# Arithmetic operators: define all the arithmetic operators here --
#pop the 2 values from opstack, add them and push it back up the opstack
def add():
    val1 =0
    val2 = 0
    addition = 0
    if len(opstack) > 1:
        val1 = opPop()
        val2 = opPop()
    else: print ("wrong parameters") 
    if(isinstance(val1, int) and isinstance(val2, int)):
        addition = val1 + val2
    else: print ("wrong type")
    opPush(addition)
    pass
#pop the 2 values from opstack, subtract them and push it back up the opstack
def sub():
    val1 =0
    val2 = 0
    subtraction = 0
    if len(opstack) > 1:
        val2 = opPop()
        val1 = opPop()
    else: print ("wrong parameters") 
    if(isinstance(val1, int) and isinstance(val2, int)):
        subtraction = val1 - val2
    else: print ("wrong type")
    opPush(subtraction)
    pass
#pop the 2 values from opstack, multiply them and push it back up the opstack
def mul():
    val1 =0
    val2 = 0
    multiply = 0
    if len(opstack) > 1:
        val1 = opPop()
        val2 = opPop()
    else: print ("wrong parameters") 
    if(isinstance(val1, int) and isinstance(val2, int)):
        multiply = val1 * val2
    else: print ("wrong type")
    opPush(multiply)
    pass
#pop the 2 values from opstack, divide them and push it back up the opstack
def div():
    val1 =0
    val2 = 0
    divide = 0
    if len(opstack) > 1:
        val2 = opPop()
        val1 = opPop()
    else: print ("wrong parameters") 
    if val2 == 0:
        print("division by zero")
    else:
        if(isinstance(val1, int) and isinstance(val2, int)):
            divide = val1 / val2
        else: print ("wrong type")
    opPush(divide)
    pass
#pop the 2 values from opstack, mod them and push it back up the opstack
def mod():
    val1 =0
    val2 = 0
    module = 0
    if len(opstack) > 1:
        val2 = opPop()
        val1 = opPop()
    else: print ("wrong parameters") 
    if(isinstance(val1, int) and isinstance(val2, int)):
        module = val1 % val2
    else: print ("wrong type")
    opPush(module)
    pass




# add, sub, mul, div, mod
# Make sure to check the operand stack has the correct number of parameters and types of the parameters are correct.

#--------------------------- 15% -------------------------------------
# Array operators: define the array operators length, get
#pop the array off the opstack and push the length of array on opstack
def length():
    x = []
    num = 0
    if len(opstack) > 0:
        x = opPop()
        for i in x:
            num = num +1
        opPush(num)
    pass
#pop the array and index off the opstack and push the index value back up
def get():
    arr = []
    if len(opstack) > 1:
        number = opPop()
        arr = opPop()
        if isinstance(number, int) and isinstance(arr, list):
            opPush(arr[number])
    pass

#--------------------------- 25% -------------------------------------
# Define the stack manipulation and print operators: dup, exch, pop, roll, copy, clear, stack
#duplicate the top 2 numbers in the opstack
def dup():
    dupicate = 0
    if len(opstack) > 0:
        duplicate = opPop()
    opPush(duplicate)
    opPush(duplicate)
    pass
#exchange the top values in the stack
def exch():
    val1 = 0
    val2 = 0
    if len(opstack) > 1:
        val2 = opPop()
        val1 = opPop()
    opPush(val2)
    opPush(val1)
    pass
#pop the value off the stack
def pop():
    if len(opstack) > 0:
        opstack.pop()
    pass

def roll():
    j = 0
    l = []
    if len(opstack) > 1:
        x = opPop() #position
        y = opPop() #number of values to move
        i = 0
        if 0 < y < len(opstack):
            while i <= y:
                opstack.insert(x, opstack.pop(i))
                i = i+1
        else:
            for i in reversed(range(len(opstack))):
                while i != abs(y):
                    opstack.insert(x, opstack.pop(i))
    pass
def copy():
    l = []
    i = 0
    k = 0
    if len(opstack) > 0:
        x = opPop()
        while i < x:
            l.append(opPop())
            i = i + 1
        
        while k < 2:
            for val in reversed(l):
                opPush(val)
            k = k+1
    pass

def clear():
    while len(opstack) > 0:
        opstack.pop()
    pass
    
def stack():
    if static:
        print("Static")
    else: print("Dynamic")
    print("===============")
    opstack.reverse()
    for a in opstack:
        print(a)
    print("===============")
    opstack.reverse()
    index = len(dictstack) - 1
    dictstack.reverse()
    for (d, link) in dictstack:
        print("----", index, "---- ", end="")
        if static:
            print(link, "----", end="")
        print()
        for (k, v) in d.items():
            print(k, " [", v, "]", sep="")
        index -= 1
    dictstack.reverse()
    print("===============")
pass



#--------------------------- 20% -------------------------------------
# Define the dictionary manipulation operators: dict, begin, end, psDef
# name the function for the def operator psDef because def is reserved in Python
# Note: The psDef operator will pop the value and name from the stack and call
# your own "define" operator (pass those values as parameters). Note that psDef() won't have any parameters.

#def psDict():
#    if len(opstack) > 0:
#        num = opPop()
#        d = dict.fromkeys(range(num))
#        opPush(d)
#    pass

#def begin():
#    d = {}
#    if len(opstack) > 0:
#        d = opPop()
#    dictPush(d)
#    pass

#def end():
#    dictPop()
#    pass

#--------------------------------------test Functions-----------------------
# all the test functions
#def testLookup():
#    clear()
#    opPush("\n1")
#    opPush(3)
#    psDef()
    
#    if lookup("n1") != 3: return False
#    return True 

#def testAdd():
#    clear()
#    opPush(2)
#    opPush(3)
#    add()
#    if opPop() != 5: return False
#    else: return True
#    pass

#def testsub():
#    clear()
#    opPush(2)
#    opPush(1)
#    sub()
#    if opPop() != 1: return False
#    else: return True
#    pass

#def testmul():
#    clear()
#    opPush(3)
#    opPush(3)
#    mul()
#    if opPop() != 9: return False
#    else: return True
#    pass

#def testdiv():
#    clear()
#    opPush(10)
#    opPush(2)
#    div()
#    if opPop() != 5: return False
#    else: return True
#    pass

#def testmod():
#    clear()
#    opPush(55)
#    opPush(7)
#    mod()
#    if opPop() != 6: return False
#    else: return True
#    pass

#def testlength():
#    clear()
#    opPush([1, 2, 3, 4, 5])
#    length()
#    if opPop() != 5: return False
#    else: return True
#    pass

#def testget():
#    clear()
#    opPush(3)
#    opPush([1, 2, 3, 4, 5])
#    get()
#    val1 = opPop()
#    if val1 != 4: return False
#    else: return True
#    pass

#def testdup():
#    clear()
#    opPush(10)
#    opPush(20)
#    opPush(30)
#    dup()
#    val1 = opPop()
#    val2 = opPop()
#    if val1 == 30 and val2 == 30: return True
#    else: return False
#    pass

#def testexch():
#    clear()
#    opPush(10)
#    opPush(20)
#    opPush(30)
#    exch()
#    if opPop() == 20: return True
#    else: return False
#    pass

#def testroll():
#    clear()
#    opPush(10)
#    opPush(20)
#    opPush(30)
#    opPush(40)
#    opPush(2)
#    opPush(3)
#    roll()
#    if opstack == [20, 40, 30, 10]: return True
#    else: return False
#    pass

#def testcopy():
#    clear()
#    opPush(10)
#    opPush(20)
#    opPush(30)
#    opPush(40)
#    opPush(2)
#    copy()
#    if opstack == [10, 20, 30, 40, 30, 40]: return True
#    else: return False
#    pass

#def testclear():
#    clear()
#    opPush(10)
#    opPush(20)
#    opPush(30)
#    opPush(40)
#    opPush(2)
#    clear()
#    if opstack == []: return True
#    else: return False
#    pass

#def testbegin():
#    test_dict = {'firstname': 'hasnain', 'value': 5}
#    opPush(test_dict)
#    begin()
#    popped_dict = dictstack.pop()
#    if test_dict != popped_dict:
#        return False
#    return True

#def testend():
#    test_dict = {'name': 'hasnain', 'value': 5}
#    dictPush(test_dict)
#    end()
#    if dictstack.__contains__(test_dict):
#        return False
#    return True

#def testpsDef():
#    clear()
#    test_dict = {'name': 'hasnain', 'value': 5}
#    dictPush(test_dict)
#    opPush(6)
#    opPush("/khan")
#    psDef()
#    test_result = {'name': 'khan', 'value': 6}
#    final_dict = dictstack.pop()
#    if final_dict != test_result:
#        return False
#    return True


#test cases
#testCases = [('add', testAdd), ('sub', testsub), ('div', testdiv), ('mul', testmul), ('mod', testmod),
#             ('length', testlength),('dup', testdup), ('exch', testexch), ('roll', testroll),
#             ('copy', testcopy), ('clear', testclear),('begin', testbegin), ('end', testend)]

#failedTests = [testName for (testName, testProc) in testCases if not testProc()]
#if failedTests:
#   print('Some tests failed', failedTests)
#else:
#   print('All tests are OK')


#PART 2

#-------------------------1. Convert all the string to a list of tokens.------------------------------------------------#
# For tokenizing we'll use the “re” package for Regular Expressions.


def tokenize(s):
    retValue = re.findall("/?[a-zA-Z][a-zA-Z0-9_]*|[[][a-zA-Z0-9_\s!][a-zA-Z0-9_\s!]*[]]|[-]?[0-9]+|[}{]+|%.*|[^ \t\n]", s)
    return retValue



#-------------------------2. Convert the token list to a code array ------------------------------------------------#
# Write your parsing code here; it takes a list of tokens produced by tokenize
# and returns a code array; Of course you may create additional functions to help you write parse()

#function that takes in a string, convert it to int and return true if it does else false
def isnumber(s):
    try:
        int(s)
    except ValueError:
        return False
    return True

#function that takes a list of string tokens, looks for matching 
#curly braces in the token list, recursively converts the tokens between
#matching curly braces into code arrays (sub-lists of tokens)
def parse(tokens):
    res = list()
    
    i = 0
    while i < len(tokens):
        token = tokens[i]
        #check if the string contains a number
        if isnumber(token):
            res.append(int(token))
        #check if the string contians an array
        elif token[0] == '[':
            newList = list()
            number_string = token.split('[', 1)[1].split(']')[0]
            number_list = number_string.split(' ')
            for j in number_list:
                if isnumber(j):
                    newList.append(int(j))
            res.append(newList)
        #check if the token is open curly braces
        elif token == '{':
            parsed_token, index = parse(tokens[i + 1:])
            res.append(parsed_token)
            i += index + 1
        #check if the token is closed curly braces
        elif token == '}':
            return res, i
        #else append the token on the list
        else:
            res.append(token)
        #iterate through list
        i += 1
    #return list
    return res
    pass

#Forloop function that pops 4 values off the stac
#codeArray, endValue, incrementalValue, and startValue and call the function specified in code array
def For():
    codeArray = list()
    if len(opstack) > 3:
        codeArray = opPop()
        endValue = opPop()
        incrementalValue = opPop()
        startValue = opPop()
        #while startvalue is not equal endValue
        while (startValue != endValue):
            opPush(startValue)
            for i in codeArray:
                if isinstance(i, int):
                    opPush(i)
                #call the function specified in code array
                else:
                    if i == 'def':
                        psDef()
                    elif i == 'add':
                        add()
                    elif i == 'sub':
                        sub()
                    elif i == 'mul':
                        mul()
                    elif i == 'div':
                        div()
                    elif i == 'mod':
                        mod()
                    elif i == 'length':
                        length()
                    elif i == 'get':
                        get()
                    elif i == 'dup':
                        dup()
                    elif i == 'exch':
                        exch()
                    elif i == 'pop':
                        pop()
                    elif i == 'roll':
                        roll()
                    elif i == 'copy':
                        copy()
                    elif i == 'clear':
                        clear()
                    elif i == 'stack':
                        stack()
                    elif i == 'dict':
                        psDict()
                    elif i == 'begin':
                        begin()
                    elif i == 'end':
                        end()
            #update the start value
            if incrementalValue > 0:
                startValue -= incrementalValue
            else:
                startValue += incrementalValue

    pass

#function that implements forall operator of postscript
def ForAll():
    codeArray = list()
    if len(opstack) > 1:
        codeArray = opPop()
        arr = opPop()
        #for all the elements in the array do the operation specified in code array
        for i in codeArray:
                if isinstance(i, int):
                    opPush(i)
                else:
                    if i == 'add':
                        num = opPop()
                        for a in arr:
                            ans = num + a
                            opPush(ans)
                    elif i == 'sub':
                        num = opPop()
                        for s in arr:
                            ans = num - s
                            opPush(ans)
                    elif i == 'mul':
                        num = opPop()
                        for m in arr:
                            ans = num * m
                            opPush(ans)
                    elif i == 'div':
                        num = opPop()
                        for d in arr:
                            ans = num / d
                            opPush(ans)
                    elif i == 'mod':
                        num = opPop()
                        for m in arr:
                            ans = num % m
                            opPush(ans)
    pass
#-------------------------3. Interpret code arrays------------------------------------------------#
def getInput():
    userInput = input("Static scoping or dynamic scoping: ")
    global static
    if userInput == "static":
        static = True
    else:
        static = False
pass


#Function that takes a code array as argument, and changes the
#state of the operand and dictionary stacks according to what it finds there, doing any output indicated
#by the SPS program (using the stack operator) along the way. Note that your interpret function
#needs to be recursive: interpret will be called recursively when a name is looked up and its value is a
#code array
def interpret(code): # code is a code array
        operatorList = ['def', 'add', 'sub', 'mul', 'div', 'mod', 'length', 'get', 'dup',
                        'exch', 'pop', 'roll', 'copy', 'clear', 'stack', 'dict', 'begin', 'end', 'for', 'forall']
        if isinstance(code, int):
                opPush(code)
        else:
            for token in code:
                #check if the token is a number
                if isinstance(token, int):
                    opPush(token)
                #check if the token is a string
                elif isinstance(token, str):
                    if token[0] == '/':
                        opPush(token[1:])
                    elif token in operatorList:
                         if token == 'def':
                             psDef()
                         elif token == 'add':
                             add()
                         elif token == 'sub':
                             sub()
                         elif token == 'mul':
                             mul()
                         elif token == 'div':
                             div()
                         elif token == 'mod':
                             mod()
                         elif token == 'length':
                             length()
                         elif token == 'get':
                             get()
                         elif token == 'dup':
                             dup()
                         elif token == 'exch':
                             exch()
                         elif token == 'pop':
                             pop()
                         elif token == 'roll':
                             roll()
                         elif token == 'copy':
                             copy()
                         elif token == 'clear':
                             clear()
                         elif token == 'stack':
                             stack()
                         #elif token == 'dict':
                         #    psDict()
                         #elif token == 'begin':
                         #    begin()
                         #elif token == 'end':
                         #    end()
                         elif token == 'for':
                             For()
                         elif token == 'forall':
                             ForAll()
                    else:
                        code = lookup(token)
                        link = 1
                        if static:
                            link = getLink(token)
                        dictPush({}, link)
                        interpret(code)
                        dictPop()
                else:
                    opPush(token)
pass 


#-------------------------4. Interpret the SPS code------------------------------------------------#
#function that treats a string as an SPS program and interpretsit.
def interpreter(s): # s is a string
    interpret(parse(tokenize(s))) 
    pass



#-------------------------TESTING------------------------------------------------#


getInput()
#print("TEST 1 - function using for loop")
interpreter(
"""/x 4 def
/g { x stack } def
/f { /x 7 def g } def
f""")
print()
print("-------TEST CASE 2-------")
clear()

interpreter(
"""/m [25 50] 1 get def
/n [100 1] 0 get def
/egg1 {/m 25 def n} def
/chic {
 /n 1 def
 /egg2 { n } def
 m n
 egg1
 egg2
 stack } def
n
chic""")
