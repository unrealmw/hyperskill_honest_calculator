
messages = {            # messages database
    "msg_0": "Enter an equation",
    "msg_1": "Do you even know what numbers are? Stay focused!",
    "msg_2": "Yes ... an interesting math operation. You've slept through all classes, haven't you?",
    "msg_3": "Yeah... division by zero. Smart move...",
    "msg_4": "Do you want to store the result? (y / n):",
    "msg_5": "Do you want to continue calculations? (y / n):",
    "msg_6": " ... lazy",
    "msg_7": " ... very lazy",
    "msg_8": " ... very, very lazy",
    "msg_9": "You are",
    "msg_10": "Are you sure? It is only one digit! (y / n)",
    "msg_11": "Don't be silly! It's just one number! Add to the memory? (y / n)",
    "msg_12": "Last chance! Do you really want to embarrass yourself? (y / n)",
}

operations = ["*", "/", "+", "-"]       # operators list

M = 0   # memory variable


def input_equation():

    """Gets equation from input and splits it on two variables and operator"""

    x, oper, y = input().split()
    return x, oper, y


def converting_to_float(a: str):

    """Gets number as a string and then converts in to float.
    If variable is not numeric prints msg_1 from messages database"""

    try:
        a = float(a)
        return a
    except ValueError:
        print(messages["msg_1"])


def checking_operator(operator):

    """Checks operator. If it in operations database return True,
    else prints msg_2 from messages database and return False"""

    if operator in operations:
        return True
    else:
        print(messages["msg_2"])
        return False


def math_calculations(a, b, operator):

    """Calculating the equation. If second value is zero, program prints msg_3. And return the result."""

    result = None
    if operator == operations[0]:
        result = a * b
    elif operator == operations[2]:
        result = a + b
    elif operator == operations[3]:
        result = a - b
    elif operator == operations[1] and b != 0:
        result = a / b
    elif operator == operations[1] and b == 0:
        print(messages["msg_3"])
    return result


def from_memory(a):

    """If variable equal to M, program get num from memory and replaces that variable to value from memory"""

    if a == "M":
        a = M
    return a


def saving_result_to_memory(result: float):

    """This program check variable is one-digit number.
    If it is asks 3 times does the user wants to save it?"""

    global M
    index = 10
    msg = "msg_"
    choice = input(messages["msg_4"])
    if choice == "y":
        if is_one_digit(result):
            while True:
                msg_index = msg + str(index)
                choice = input(messages[msg_index])
                if choice == "y":
                    if index < 12:
                        index += 1
                    else:
                        M = result
                        break
                elif choice == "n":
                    break
                else:
                    continue
        else:
            M = result
        program_continuer()
    elif choice == "n":
        program_continuer()


def program_continuer():

    """Continues program from the beginning if choice is 'y'"""

    choice = input(messages["msg_5"])
    if choice == "y":
        calc()


def is_one_digit(num: float):

    """Return True if num is one-digit number."""

    output = False
    if num.is_integer() and -10 < int(num) < 10:
        output = True
    return output


def check(v1, v2, operator):

    """Checking user for laziness"""

    msg = ""
    if is_one_digit(v1) and is_one_digit(v2):
        msg += messages["msg_6"]
    if (v1 == 1 or v2 == 1) and operator == "*":
        msg += messages["msg_7"]
    if (v1 == 0 or v2 == 0) and operator in ["*", "+", "-"]:
        msg += messages["msg_8"]
    if msg != "":
        msg = messages["msg_9"] + msg
        print(msg)


def calc():
    
    """Main body of the calculator program."""
    
    print(messages["msg_0"])
    x, oper, y = input_equation()
    x = from_memory(x)
    y = from_memory(y)
    x = converting_to_float(x)
    y = converting_to_float(y)
    result = None
    if checking_operator(oper):
        check(x, y, oper)
        result = math_calculations(x, y, oper)
    if result is not None:
        print(result)
        saving_result_to_memory(result)


if __name__ == '__main__':
    calc()
