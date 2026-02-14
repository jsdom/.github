# Security Policy

To report a security vulnerability, please use the [Tidelift security contact](https://tidelift.com/security). Tidelift will coordinate the fix and disclosure.

## ReDOS

None of the jsdom projects consider the so-called "ReDOS" family of "vulnerabilities" to be security problems.

The jsdom projects, by their nature, accept complicated inputs, as they are attempting to emulate a web browser. The fact that performance on some inputs can be slower than others is a natural consequence of this. We do not support running them without pre-vetting your inputs to be sure that they will cause acceptable performance for your use case. And as such, we do not recognize it as a security vulnerability if certain inputs trigger longer regular expression execution times.

If you would like to improve performance on certain inputs, a pull request will be accepted. But no security bounties or CEVs will be issued for these performance issues.

You can read more about ReDOS in the article ["ReDOS 'vulnerabilities' and misaligned incentives"](https://blog.yossarian.net/2022/12/28/ReDoS-vulnerabilities-and-misaligned-incentives).

## Script execution threat model

jsdom's `runScripts` option controls whether web content (inline scripts, event handler attributes, etc.) embedded in the HTML being processed will execute. The security model is:

- **Without `runScripts: "dangerously"`**, untrusted HTML passed to jsdom will not cause script execution. You can safely process arbitrary web content from the internet.
- **With `runScripts: "dangerously"`**, you are trusting the HTML content, and it can run arbitrary Node.js code.

This protection applies to the web content being processed. It does not apply when the host Node.js environment is already compromised. If an attacker can execute arbitrary code in your Node.js process, modify JavaScript built-in prototypes, or access jsdom's internal implementation objects, they can trivially cause script execution regardless of the `runScripts` setting — but at that point, they do not need jsdom to do so.

We do not consider reports of the form "with host-level access, you can bypass `runScripts`" to be security vulnerabilities. We may still fix individual issues as code quality improvements, but they will not receive CVEs or security advisories.
