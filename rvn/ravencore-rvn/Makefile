all:
	git clone https://github.com/underdarkskies/ravencore
	cd ravencore && git checkout 97785c0b6298155a3f90b118c29d24f9da3b14e1
	cd ravencore && rm -rf .git # Delete .git folder to reduce space
	cd ravencore && yarn
	rm -rf ravencore/node_modules/ravencore-node/bin/*.gz
	rm -rf ravencore/node_modules/ravencore-node/bin/bitcoin-*/bin/bitcoin-qt
	rm -rf ravencore/node_modules/ravencore-node/bin/bitcoin-*/bin/test_bitcoin
	rm -rf ravencore/node_modules/ravencore-node/test/*

clean:
	rm -fr ravencore
