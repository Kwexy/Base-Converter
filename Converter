import tkinter
import math

dec = 255
bin = ""
hex = ""

#hextable reference for functions
hexTable = {0: "0",
                1: "1",
                2: "2",
                3: "3",
                4: "4",
                5: "5",
                6: "6",
                7: "7",
                8: "8",
                9: "9",
                10: "a",
                11: "b",
                12: "c",
                13: "d",
                14: "e",
                15: "f",
                }
#hexlist references for key lookup
hexKeyList = list(hexTable.keys())
hexValList = list(hexTable.values())

def decConvert():
    binText.delete(0, len(binText.get()))
    hexText.delete(0, len(hexText.get()))
    try:
        if int(decText.get()) > 0:
            binText.insert(0, convDecToBin(int(decText.get())))
            hexText.insert(0, convDecToHex(int(decText.get())))
        else:
            binText.insert(0, "0")
            hexText.insert(0, "0")
    except (ValueError, TypeError):
        binText.insert(0, "0")
        hexText.insert(0, "0")


def binConvert():
    dec = convBinToDec(str(binText.get()))
    decText.delete(0, len(decText.get()))
    hexText.delete(0, len(hexText.get()))
    try:
        decText.insert(0, int(dec))
        hexText.insert(0, convDecToHex(dec))
    except:
        ValueError

def hexConvert():
    decText.delete(0, len(decText.get()))
    binText.delete(0, len(binText.get()))
    try:
        dec = convHexToDec(hexText.get())
        decText.insert(0, int(dec))
        binText.insert(0, convDecToBin(dec))
    except ValueError:
        decText.insert(0, "0")
        binText.insert(0, "0")



def isOdd(num):
    if num % 2 == 0:
        return False
    else:
        return True

def convDecToBin(num):
    placeDec = 1
    bin = ""
    while num / placeDec >= 1:
        if isOdd(math.floor(num / placeDec)):
            bin = "1" + bin
        else:
            bin = "0" + bin
        placeDec *= 2
    return bin

def convBinToDec(bin):
    if bin == "1":
        return 1
    dec = 0
    for num in range(len(bin)-1, -1, -1):
        if bin[num] == "1":
            dec+=math.pow(2, num)
        elif bin[num] != "1" or bin[num] != "0":
            return 0
    return dec

def convDecToHex(num):
    symbol = num % 16
    base = num // 16
    if base == 0:
        return hexTable.get(symbol)
    return convDecToHex(base) + hexTable.get(symbol)

def convHexToDec(hex):
    dec = 0
    base = 1
    for count in range(len(hex)-1, -1, -1):
        decVal = hexValList.index(hex[count])
        dec += hexKeyList[decVal]*base
        base *= 16
    return dec

tk = tkinter.Tk()
tk.title("Base Converter")
tk.geometry("260x100")
tk.resizable(False, False)

leftContainer = tkinter.Frame(tk, height = 50)
middleContainer = tkinter.Frame(tk)
rightContainer = tkinter.Frame(tk)
leftContainer.pack(side = tkinter.LEFT)
middleContainer.pack(side = tkinter.LEFT)
rightContainer.pack(side = tkinter.LEFT)

decLabel = tkinter.Label(leftContainer, text = "Decimal:")
decLabel.pack(side = tkinter.TOP)
binLabel = tkinter.Label(leftContainer, text = "Binary:")
binLabel.pack()
hexLabel = tkinter.Label(leftContainer, text = "Hex:   0x")
hexLabel.pack()

decText = tkinter.Entry(middleContainer, width = 20)
decText.pack()
binText = tkinter.Entry(middleContainer, width = 20)
binText.pack()
hexText = tkinter.Entry(middleContainer, width = 20)
hexText.pack()

decButton = tkinter.Button(rightContainer, text = "Convert Dec", command = decConvert)
decButton.pack()
binButton = tkinter.Button(rightContainer, text = "Convert Bin ", command = binConvert)
binButton.pack()
hexButton = tkinter.Button(rightContainer, text = "Convert Hex", command = hexConvert)
hexButton.pack()

tk.mainloop()
