conda py27

pip install --upgrade google-api-python-client

pip install google-cloud

pip install selenium

export CHROME_SRC=/home/yuan/projects/chromium/src
export DOM_DISTILLER_DIR=/home/yuan/projects/dom-distiller

roll-distiller () {
  (
    (cd $DOM_DISTILLER_DIR && ant package) && \
    rm -rf $CHROME_SRC/third_party/dom_distiller_js/dist/* && \
    cp -rf $DOM_DISTILLER_DIR/out/package/* $CHROME_SRC/third_party/dom_distiller_js/dist/ && \
    touch $CHROME_SRC/components/resources/dom_distiller_resources.grdp
  )
}

https://chromium.googlesource.com/chromium/src.git/+/HEAD/docs/linux/build_instructions.md#Get-the-code

https://blog.csdn.net/weixin_42307427/article/details/108483941

python build/util/lastchange.py -o LASTCHANGE