deps: hexbyte.py pip lightblue-install

hexbyte.py:
	curl -sL https://raw.githubusercontent.com/borismus/Running-Gestures/master/hexbyte.py > hexbyte.py

pip:
	@echo ">> Installing pip"
	pip --version &>/dev/null || \
		sudo easy_install pip
	@echo

lightblue:
	@echo ">> Installing lightblue"
	[[ -d lightblue-0.4 ]] || (\
		git clone https://github.com/postskolkovo/lightblue-0.4 &&\
		cd lightblue-0.4 && patch < ../setup.py.patch \
	)
	@echo

lightblue-install: pyobjc-framework-Cocoa lightblue
	cd lightblue-0.4 && sudo python setup.py install

pyobjc-framework-Cocoa: pyobjc-core
	@echo ">> Installing pyobjc-framework-Cocoa"
	sudo pip install -U pyobjc-framework-Cocoa
	@echo

pyobjc-core:
	@echo ">> Installing pyobjc-core"
	sudo pip install -U pyobjc-core
	@echo

setuptools:
	@echo ">> Upgrading setuptools"
	sudo pip uninstall setuptools
	curl https://bootstrap.pypa.io/ez_setup.py | python
	@echo

uninstall:
	sudo pip uninstall pyobjc-core 2>/dev/null || echo "Not installed"
	sudo pip uninstall pyobjc-framework-Cocoa 2>/dev/null || echo "Not installed"
	sudo pip uninstall lightblue 2>/dev/null || echo "Not installed"

clean:
	rm -f *.pyc
	rm -f hexbyte.py
	rm -rf lightblue-0.4
	rm -rf pyobjc-core
