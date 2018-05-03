all:
	git clone https://github.com/underdarkskies/ravencore
	cd ravencore && git checkout 86075c9dd811d6a6b438078d7c127bd858992bf1
	cd ravencore && rm -rf .git # Delete .git folder to reduce space
	cd ravencore && yarn
	rm -rf ravencore/node_modules/ravencore-node/bin/*.gz
	rm -rf ravencore/node_modules/ravencore-node/bin/bitcoin-*/bin/bitcoin-qt
	rm -rf ravencore/node_modules/ravencore-node/bin/bitcoin-*/bin/test_bitcoin
	rm -rf ravencore/node_modules/ravencore-node/test/*

clean:
	rm -fr ravencore
