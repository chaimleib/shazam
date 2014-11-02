deps: hexbyte.py lightblue-install

hexbyte.py:
	curl -sL https://raw.githubusercontent.com/borismus/Running-Gestures/master/hexbyte.py > hexbyte.py

lightblue:
	[[ -d lightblue-0.4 ]] ||\
		git clone https://github.com/postskolkovo/lightblue-0.4 &&\
		cd lightblue-0.4 && patch < ../setup.py.patch

lightblue-install: lightblue
	cd lightblue-0.4 && sudo python setup.py install

clean:
	rm -f hexbyte.py
	rm -rf lightblue-0.4