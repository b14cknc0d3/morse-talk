..  -*- coding: utf-8 -*-

.. currentmodule:: morse_talk

Start here to begin working with Morse Talk.


Encode a message
----------------

Create a message you want to encode.

>>> import morse_talk as mtalk
>>> message = "Hi, I'll be there by 10 PM"


``message`` is a Python string. No leading or trailing
whitespaces are allowed in it. Even if it is there, it
will be truncated off for encoding.

Now encode your message in Morse Code.

>>> code = mtalk.encode(message)
>>> code
'....   ..   --..--       ..   .----.   .-..   .-..       -...   .       -   ....   .   .-.   .       -...   -.--       .----   -----       .--.   --'

.. Note::
	Morse Talk supports alphabets, numerals and some special 
	characters only. If any unsupported character is present
	in the ``message``, it will be ignored.

	>>> message = "Congratualtion!"
	>>> mtalk.encode(message)
	WARNING: Unsupported characters in the string
	'-.-.   ---   -.   --.   .-.   .-   -   ..-   .-..   .-   -   ..   ---   -.   ...'

You can also encode the message in binary encoding style.

>>> mtalk.encode(code, 'binary')


Decode a message
----------------

Decode the message which you have encoded in Morse Code.

>>> code = '.-   .-..   .--.   ....   .-       ....-   .....       -..   .   .--.   .-   .-.   -   .   -..'
>>> message = mtalk.decode(code)
>>> message
'alpha 45 departed'

Decoding a binary message is brainstorming right now. If we think further,
there can be multiple messages for a single code. So currently, Morse Talk
does not support binary decoding.

>>> code = '11100011111111100011111000111110001111111111'
>>> mtalk.decode(code, 'binary')
Sorry, but it seems that binary encodings can have multiple messages. So for now, we couldn't show even one of them.

By the way, that code was generated by ``mtalk.encode('sorry', 'binary')`` ;-)