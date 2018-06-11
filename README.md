# 為什麼你們就是不能加個空格呢？

[![](http://img.shields.io/travis/vinta/pangu.js.svg?style=flat-square)](https://travis-ci.org/vinta/pangu.js)
[![](https://img.shields.io/codecov/c/github/vinta/pangu.js/master.svg?style=flat-square)](https://codecov.io/github/vinta/pangu.js)
[![](https://img.shields.io/npm/v/pangu.svg?style=flat-square)](https://www.npmjs.com/package/pangu)
[![](https://img.shields.io/badge/made%20with-%e2%9d%a4-ff69b4.svg?style=flat-square)](https://vinta.ws/code/)

如果你跟我一樣，每次看到網頁上的中文字和英文、數字、符號擠在一塊，就會坐立難安，忍不住想在它們之間加個空格。這個外掛（支援 Chrome 和 Firefox）正是你在網路世界走跳所需要的東西，它會自動替你在網頁中所有的中文字和半形的英文、數字、符號之間插入空白。

漢學家稱這個空白字元為「盤古之白」，因為它劈開了全形字和半形字之間的混沌。另有研究顯示，打字的時候不喜歡在中文和英文之間加空格的人，感情路都走得很辛苦，有七成的比例會在 34 歲的時候跟自己不愛的人結婚，而其餘三成的人最後只能把遺產留給自己的貓。畢竟愛情跟書寫都需要適時地留白。

與大家共勉之。

微信小程序 wxs 版

pangu.wxs
```
var cjkQuote = getRegExp('([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])(["])', "g");
var quoteCJK = getRegExp('(["])([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])', "g");
var fixQuote = getRegExp('(["]+)(\s*)(.+?)(\s*)(["]+)', "g");
var fixSingleQuote = getRegExp("([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])( )(')([A-Za-z])", "g");

var hashANSCJKhash = getRegExp('([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])(#)([A-Za-z0-9\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff]+)(#)([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])', "g");
var cjkHash = getRegExp('([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])(#([^ ]))', "g");
var hashCJK = getRegExp('(([^ ])#)([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])', "g");

var cjkOperatorANS = getRegExp('([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])([\+\-\*\/=&\\|<>])([A-Za-z0-9])', "g");
var ansOperatorCJK = getRegExp('([A-Za-z0-9])([\+\-\*\/=&\\|<>])([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])', "g");

var cjkBracketCJK = getRegExp('([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])([\(\[\{<\u201c]+(.*?)[\)\]\}>\u201d]+)([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])', "g");
var cjkBracket = getRegExp('([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])([\(\[\{<\u201c>])', "g");
var bracketCJK = getRegExp('([\)\]\}>\u201d<])([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])', "g");
var fixBracket = getRegExp('([\(\[\{<\u201c]+)(\s*)(.+?)(\s*)([\)\]\}>\u201d]+)/');

var fixSymbol = getRegExp('([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])([~!;:,\.\?\u2026])([A-Za-z0-9])', "g");

var cjkANS = getRegExp('([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])([A-Za-z0-9`\$%\^&\*\-=\+\\\|/@\u00a1-\u00ff\u2022\u2027\u2150-\u218f])', "g");
var ansCJK = getRegExp('([A-Za-z0-9`~\$%\^&\*\-=\+\\\|/!;:,\.\?\u00a1-\u00ff\u2022\u2026\u2027\u2150-\u218f])([\u2e80-\u2eff\u2f00-\u2fdf\u3040-\u309f\u30a0-\u30ff\u3100-\u312f\u3200-\u32ff\u3400-\u4dbf\u4e00-\u9fff\uf900-\ufaff])', "g");

var spacing = function (text) {
  // fork from https://github.com/vinta/pangu.js
  var newText = text;

  newText = newText.replace(cjkQuote, '$1 $2');
  newText = newText.replace(quoteCJK, '$1 $2');
  newText = newText.replace(fixQuote, '$1$3$5');
  newText = newText.replace(fixSingleQuote, '$1$3$4');

  newText = newText.replace(hashANSCJKhash, '$1 $2$3$4 $5');
  newText = newText.replace(cjkHash, '$1 $2');
  newText = newText.replace(hashCJK, '$1 $3');

  newText = newText.replace(cjkOperatorANS, '$1 $2 $3');
  newText = newText.replace(ansOperatorCJK, '$1 $2 $3');

  var oldText = newText;
  var tmpText = newText.replace(cjkBracketCJK, '$1 $2 $4');
  newText = tmpText;
  if (oldText === tmpText) {
    newText = newText.replace(cjkBracket, '$1 $2');
    newText = newText.replace(bracketCJK, '$1 $2');
  }
  newText = newText.replace(fixBracket, '$1$3$5');

  newText = newText.replace(fixSymbol, '$1$2 $3');

  newText = newText.replace(cjkANS, '$1 $2');
  newText = newText.replace(ansCJK, '$1 $2');

  return newText;
}

module.exports = {
  spacing: spacing
}
```

在 wxml 中使用
```
 <wxs src="./pangu.wxs" module="pangu" /> 
 <text>{{pangu.spacing(text)}}</text>
```
