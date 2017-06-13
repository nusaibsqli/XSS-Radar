<center>
<img src="https://user-images.githubusercontent.com/4115778/27087279-7ae27a2a-504c-11e7-92aa-d0aee598da00.png" height="200"></img>
</center>

XSS Radar is a tool that detects parameters and fuzzes them for [cross-site scripting](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)) vulnerabilities.
It's also the first tool developed by the [Bug Bounty Forum](https://bugbountyforum.com) community! 

## How do I install it?
At present, we're only supporting the widely used **Google Chrome**. We hope to support Firefox in the future.

1. First, `git clone https://github.com/bugbountyforum/XSS-Hamster`
2. Visit `chrome://extensions/`
3. Enable Developer Mode via the checkbox
4. Select "Load Unpacked Extension"
5. Finally, locate and select the `extension` folder

## How do I use it?
Visit a target page, open the extension and select **Fuzz!**
<img src="example.png" alt="Screenshot of extension Fuzz window" height="450"/>

## How do I contribute?
* If you're a Bug Bounty Forum member, please drop @smiegles a message so you can start contributing.
* If not, feel free to get in touch via Twitter!

### Contexts and tests
We've developed contexts – and their respective tests – in a fully modular fashion. By doing so, we've made it easy to contribute new methodologies to the Scanner module.

**Contexts** are found in `contexts.js` (inside `extension/src/payloads/`). Upon fuzzing, the Scanner searches for applicable contexts on the target and deploys the right payloads. For instance, link-based XSS bugs often rely on injection within the `href` attribute, so we've added a context which specifically matches against these:

```
{
    'type': 'a', // link/anchor type
    'matches': ['href'], // URI attribute
    'file': 'link.js' // payload file
}
```

**Tests** are found within the `playground` subdirectory. The XSS Playground contains a variety of cross-site scripting scenarios designed to support development and ensure the tool's general effectiveness. At present, we test for classic vectors, JavaScript injection, tag breakouts, and templating vulnerabilities.

### Payloads
We've integrated the following XSS payload classes. These can be found in [**extension/src/payloads**](https://github.com/bugbountyforum/XSS-Hamster/tree/master/extension/src/payloads).

* AngularJS [template injection](http://blog.portswigger.net/2016/01/xss-without-html-client-side-template.html)
    * All versions with a vulnerable Expression Sandbox are supported
* Link-based URIs
* Script injections 
* Generic tag strings

## Who made this?
This tool is a Bug Bounty Forum project with the following contributors:
* Ibram Marzouk
* Anshuman Bhartiya
* Rafal Janicki
* Jack Cable
* Filipe Reis
* gradius
* Olivier beg
* Yasin Soliman
