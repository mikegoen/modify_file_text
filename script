import os
import sys

def get_file():
	userinput = raw_input('Enter file name, or enter "!" to list all files in current directory>')

	if userinput == "!":
		files = filter(os.path.isfile, os.listdir( os.curdir ) )
		for x in files:
			print x
		get_file()

	elif os.path.isfile(userinput) == True:
		read_lines(userinput)

	else:
		print "File not recognized"
		get_file()

#generate list from each line in file
def read_lines(filename):
	linelist = []
	try:
		with open(filename, 'r') as f:
			while True:
				line = f.readline()
				if bool(line) == False:
					break
				linelist.append(line)
	except:
		print "Failure opening/reading file, try again?"
		get_file()

	options(linelist)

def options(li):
	print "\nSelect operation on file:"
	print "1.) alphabetize lines"
	print "2.) Un-capitalize everything"
	print "3.) Capitalize everything"
	print "4.) eliminate lines with only whitespace"
	user = raw_input("Select option>")

	if user == "1":
		order_lines(li)
		new_file(li)

	if user == "2":
		newlist = map(uncap_all, li)
		new_file(newlist)

	if user == "3":
		newlist = map(cap_all, li)
		new_file(newlist)

	if user == "4":
		newlist = filter(not_whitespace, li)
		new_file(newlist)

	else:
		print "INVALID INPUT, choose a number"
		options(li)

#create file using list of strings
def new_file(li):
	namefile = raw_input("input name for new file>")
	with open(namefile, 'w') as f:
		for line in li:
			f.write(line)
	sys.exit()

#alphabetize each string in list, not case-sensitive
def order_lines(li):
	li.sort(key = lambda k : k.lower())
	return li

def not_whitespace(line):
	if not line.isspace():
		return True
	else:
		return False

def cap_all(s):
	return s.upper()
def uncap_all(s):
	return s.lower()


if __name__ == "__main__":
	get_file()
