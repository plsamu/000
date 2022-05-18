# Gitbook

```
nvm install 8
npm i -g gitbook-cli
cd test && gitbook init
gitbook build
```

{% embed url="https://github.com/GitbookIO/gitbook-cli/issues/110" %}

## Automatic build gitbook

{% embed url="https://github.com/GitbookIO/gitbook/blob/master/docs/setup.md" %}

{% hint style="danger" %}
gitbook.com support more tags than gitbook-cli... It is needed to delete them all.
{% endhint %}

### remove-unsupported-tags

```bash
#!/bin/bash

ABSPATH="$( cd -- "$(dirname "$0")" >/dev/null 2>&1 ; pwd -P )"

echo === REMOVING UNKNOWN BLOCKS ===
echo e.g. embed, hint, content

remove_unsupported_tags () {
    for file in $1/*
    do
        # file exists and is a directory
        if [ -d $file ];
        then
            remove_unsupported_tags $file
        else
            sed -i '/embed/d' $file
            sed -i '/hint/d' $file
            sed -i '/content/d' $file
        fi
    done
}

remove_unsupported_tags $ABSPATH/{reponame}   # <--- CHANGE HERE
```

### load-github

```bash
#!/bin/bash

echo === LOAD GITBOOK ===

export NVM_DIR=$HOME/.nvm
source $NVM_DIR/nvm.sh
nvm install 8
if [ $? -eq 0 ]; then
    echo OK
else
    echo FAIL: install nvm
    exit 1
fi

echo ""
which gitbook
gitbook --version
ABSPATH="$( cd -- "$(dirname "$0")" >/dev/null 2>&1 ; pwd -P )"

echo === DOWNLOAD GITBOOK ===
npm i -g gitbook-cli

echo === DOWNLOAD REPO ===
rm -rf $ABSPATH/000 2>/dev/null
git clone https://github.com/{username}/{reponame}.git  # <--- CHANGE HERE
cd $ABSPATH/{reponame}

$ABSPATH/remove-unsupported-tags

gitbook build

```

## ...

{% embed url="https://gist.github.com/chranderson/b0a02781c232f170db634b40c97ff455" %}
