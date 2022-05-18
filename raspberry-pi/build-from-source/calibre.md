# Calibre

{% embed url="https://calibre-ebook.com/download_linux" %}

{% embed url="https://github.com/kovidgoyal/calibre/blob/master/bypy/sources.json" %}

```bash
sudo apt-get install -y libpodofo-dev libhunspell-dev libstemmer-dev libmtp-dev

# for python3
sudo apt-get install python3-pip
pip install PyQt5-sip PyQtWebEngine
sudo apt-get install python3-pyqt5
sudo apt-get install python3-sipbuild python3-pyqtbuild

# for python2
sudo apt-get install python-pyqt5   
```

### fkn hell, drop here

{% hint style="danger" %}
\-c: Unable to find file "QtWidgets/QtWidgetsmod.sip"
{% endhint %}

### ...

```
curl https://bootstrap.pypa.io/pip/2.7/get-pip.py --output get-pip.py
sudo python2 get-pip.py
pip2 install ssl
```
