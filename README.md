================================================================
Introduction:
==============================

Captcha Intruder is an automatic pentesting tool to bypass captchas.

CIntruder is released under the terms of the General Public License v3 and 
is copyrighted by psy (root@lordepsylon.net - epsylon@riseup.net).

================================================================
Options and features:
==============================
 
cintruder [OPTIONS] 

Options:
  --version          show program's version number and exit
  -h, --help         show this help message and exit
  -v, --verbose      active verbose mode output results
  --proxy=PROXY      use proxy server (tor: http://localhost:8118)
  --track=TRACK      download a number of captchas from url (to: 'inputs/')
  --train=TRAIN      apply common OCR techniques to captcha
  --crack=CRACK      brute force using local dictionary (from: 'iconset/')
  --xml=XML          export result to xml format

  Advanced OCR (training):
    --set-id=SETIDS  set colour's id manually (use -v for details)
    --editor         launch an editor to apply image filters

  Modules (training):
    --list           list available modules (from: 'core/mods/')
    --mod=NAME       train using a specific OCR exploiting module

  Handlering (cracking):
    --tool=COMMAND   replace suggested word on commands of another tool. use
                     'CINT' marker like flag (ex: 'txtCaptcha=CINT')

  CIntruderNet ('http://cintruder.sf.net/cinet'):
    --send-net       send resolved captcha to CIntruderNet
    --view-net       visit distributed online dictionary website

================================================================
Examples of usage:
==============================

* Simple crack from file:

$ python cintruder --crack "captcha.gif"
-------------------
* Simple crack from URL:

$ python cintruder --crack "http://host.com/path/captcha.gif"
-------------------
* Simple crack, exporting results to xml file

$ python cintruder --crack "captcha.gif" --xml "test.xml"
-------------------
* Simple crack, with proxy TOR and verbose output

$ python cintruder --crack "http://host.com/path/captcha.gif" --proxy="http://127.0.0.1:8118" -v
-------------------
* Train captcha(s) from url, with proxy TOR and verbose output

$ python cintruder --train "http://host.com/path/captcha.gif" --proxy "http://127.0.0.1:8118" -v
-------------------
* Track 50 captcha(s) from url with proxy TOR

$ python cintruder --track "http://host.com/path/captcha.gif" "50" --proxy "http://127.0.0.1:8118"
-------------------
* List available modules (from core/mods/)

$ python cintruder --list
-------------------
* Launch an OCR module to train a specific local captcha

$ python cintruder --train "inputs/easycaptcha.gif" --mod easy
-------------------
* Launch an OCR module to crack a specific online captcha, with verbose output

$ python cintruder --crack "http://host.com/path/captcha.gif" --mod easy -v
-------------------
* Replace suggested word by CIntruder after cracking, on input commands of another tool (ex: XSSer)

$ python cintruder --crack "http://host.com/path/captcha.gif" --tool "xsser -u  http://host.com/path/param1=foo&param2=bar&txtCaptcha=CINT"
-------------------
* Send online captcha cracked to distributed online dictionary (CInet)

$ python cintruder --crack "http://host.com/path/captcha.gif" --send-net
-------------------
* Visit distributed online dictionary (CInet) website (http://cintruder.sf.net/cinet)

$ python cintruder --view-net

