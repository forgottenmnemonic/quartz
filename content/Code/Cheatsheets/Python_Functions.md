## print
```python
print("hello")
```

### Validation
## Get valid integer function
```python
def get_integer(prompt="Please enter an integer: "):  
    """  
    Function to prompt for and return a valid integer.    :param prompt: string Optional string to use as prompt    :return: integer Valid integer  
    """    num = 0  
    while True:  
        try:  
            num = int(input(prompt))  
            return num  
        except:  
            print("Invalid integer.")
```

## Get valid float
```python
def get_real(prompt="Please enter an real number: "):  
    """  
    Function to prompt for and return a valid real number    :param prompt: string Optional string to use as prompt    :return: float Valid real number  
    """    num = 0.0  
    while True:  
        try:  
            num = float(input(prompt))  
            return num  
        except:  
            print("Invalid number.")
```

## Get string
```python
def get_string(prompt=""):  
    """  
    Function to prompt for and return a string of characters.    An empty string is invalid input.    :param prompt: string Optional string to use as prompt    :return: string Non-empty string of characters  
    """    chars = ""  
    while True:  
        chars = input(prompt)  
        if chars != "":  
            return chars  
        else:  
            print("Invalid string.")
```

## Get yes or no
```python
def get_y_or_n(prompt="Please enter 'y' or 'n': "):  
    """  
    Function to prompt for and return 'y' or 'n'.    'Y', 'N', and all cases of 'yes' and 'no' are accepted.    :param prompt: string Optional string to use as prompt    :return: string Non-empty string of characters  
    """    answer = ""  
    answer = input(prompt)  
    answer = answer.lower()  
  
    while answer != "n" and answer != "y" and answer != "no" and answer != \  
            "yes":  
        print("Invalid response.")  
        answer = input(prompt)  
        answer = answer.lower()  
  
    return answer[0]
```

## Get male or female
```python
def get_m_or_f(prompt="Please enter 'm' or 'f': "):  
    """  
    Function to prompt for and return 'm' or 'f'.    'M', 'F' are accepted.    :param prompt: string Optional string to use as prompt    :return: string Non-empty string of characters  
    """    answer = ""  
    answer = input(prompt)  
  
    while answer != "m" and answer != "f" and answer != "M" and answer != "F":  
        print("Invalid response. Please enter a M for male and F for female")  
        answer = input(prompt)  
        answer = answer.upper()  
  
    return answer[0]
```

## Get integer between 1 and 6
```python
def get_activity(prompt="Please enter an integer: "):  
    """  
    Function to prompt for and return a valid integer in appropriate range.    :param prompt: string Optional string to use as prompt    :return: integer Valid integer  
    """    num = 0  
    while True:  
        try:  
            num = int(input(prompt))  
            if num in range(1, 6):  
                return num  
            else:  
                print("Invalid entry.  Please select a number from 1 to 5")  
        except:  
            print("Invalid Choice")
```