# CE2---Python
# Exercício 174
def find_gcd(a, b):
    if b == 0:
        return a
    else:
        c = a % b
        return find_gcd(b, c)


if __name__ == '__main__':
    print(find_gcd(0, 10))
   
# Exercício 175
def decimalbi(n):
    res = ''
    if n == 0:
        return 0
    if n == 1:
        res = str(1) + res
        return res
    elif n > 0 and isinstance(n, int):
        r = n % 2
        res = str(r) + res
        n = n // 2
        return decimalbi(n) + res
    else:
        return 'Error: the number must be a positive integer'


def main():
    try:
        number = int(input('Enter a positive integer: '))
        print(decimalbi(number))
    except:
        print('Please, enter an integer')


if __name__ == '__main__':
    main()
    
# Exercício 176
def phospelling(s):
    spelling = ''

    d = {'A': 'Alpha', 'B': 'Bravo', 'C': 'Charlie', 'D': 'Delta', 'E': 'Echo',\
         'F': 'Foxtrot', 'G': 'Golf', 'H': 'Hotel', 'I': 'India', 'J': 'Juliet',\
         'K': 'Kilo', 'L': 'Lima', 'M': 'Mike', 'N': 'November', 'O': 'Oscar',\
         'P': 'Papa', 'Q': 'Quebec', 'R': 'Romeo', 'S': 'Sierra', 'T': 'Tango',\
         'U': 'Uniform', 'V': 'Victor', 'W': 'Whiskey', 'X': 'Xray', 'Y': 'Yankee',\
         'Z': 'Zulu'}

    if s == '':
        return ''

    element = s[0].upper()
    if element in d:
        spelling += d[element] + ' '

    return spelling + phospelling(s[1:])


def main():
    word = input('Enter a word to spell: ')
    print(phospelling(word))


if __name__ == '__main__':
    main()
# Exercício 177
def romanv(s):
    if s == 'M':
        return 1000
    elif s == 'D':
        return 500
    elif s == 'C':
        return 100
    elif s == 'L':
        return 50
    elif s == 'X':
        return 10
    elif s == 'V':
        return 5
    elif s == 'I':
        return 1
    else:
        raise ValueError('Not a valid roman numeral')


def romaninteger(roman):
    if roman == '':
        return 0

    if len(roman) == 1:
        return romanv(roman)

    preceding = romanv(roman[0])
    following = romanv(roman[1])

    if preceding >= following:
        return preceding + romaninteger(roman[1:])

    elif preceding < following:
        return (following - preceding) + romaninteger(roman[2:])


if __name__ == '__main__':
    romannumber = input('Enter a roman number: ')
    print(romaninteger(romannumber))

# Exercício 182
symbols = []
elements = []
inf = open('../files/elements.txt', 'r')
alllines = inf.readlines()

for el in all_lines:
    symbol = el.split(',')[1]
    element = el.split(',')[2].strip()
    symbols.append(symbol)
    elements.append(element)

print(symbols)
print(elements)

res = ''


def symbolWord(string, symb_list):
    global res

    if string == '':
        return res

    else:
        if string[:3].capitalize() in symb_list:
            res += symb_list[symb_list.index(string[:3].capitalize())]
            string = string[3:]
            return symbolWord(string, symb_list)

        elif string[:2].capitalize() in symb_list:
            res += symb_list[symb_list.index(string[:2].capitalize())]
            string = string[2:]
            return symbolWord(string, symb_list)

        elif string[:1].capitalize() in symb_list:
            res += symb_list[symb_list.index(string[:1].capitalize())]
            string = string[1:]
            return symbolWord(string, symb_list)

        else:
            return False


if __name__ == '__main__':

    for element in elements:
        res = ''
        output = symbolWord(element, symbols)
        if output:
            print()
            print(element, 'Can be spelled as:')
            print(output)
            
# Exercício 185
def decode(data):
    if len(data) == 0:
        return []
    else:
        current = list(data[0] * data[1])
        return current + decode(data[2:])

def main():
    mylist = ['A', 3, 'B', 2, 'C', 6, 'D', 1, 'E', 5]
    print(decode(mylist))


if __name__ == '__main__':
    main()
