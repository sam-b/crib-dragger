#!/usr/bin/env python

import array
import optparse
import sys
def xor_all(key,target):
	key_len = len(key)
	out = ""
	for j in xrange(len(target)):
		if 31 < (target[j] ^ key[j % key_len]) < 127:
			out+=chr(target[j] ^ key[j % key_len])
		else:
			out+='_' + str(target[j])
	return out

def main():
	parser = optparse.OptionParser("Usage: ./one_time.py -c 'string' -t 'path'")
	parser.add_option('-c', dest='crib', type='string', help='specify crib string') 	
	parser.add_option('-t', dest='target', type='string', help='specify target file')
	(options, args) = parser.parse_args()
	if options.crib == None or options.target == None:
		print parser.usage
		sys.exit(0)
	target_file = open(options.target).read()
	target = bytearray(target_file)
	crib = options.crib
	for i in range((len(target)-len(crib))+1):
		key = []
		out = ''
		for j in range(len(crib)):
			key.append(target[i + j] ^ ord(crib[j]))
		xor_all(key,target)
		print out + str(key)

	key = []
	out = xor_all(key,target)
	print out
if __name__ == "__main__":
	main()
