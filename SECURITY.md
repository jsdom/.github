# Security Policy

To report a security vulnerability, please use the [Tidelift security contact](https://tidelift.com/security). Tidelift will coordinate the fix and disclosure.

## ReDOS

None of the jsdom projects consider the so-called "ReDOS" family of "vulnerabilities" to be security problems.

The jsdom projects, by their nature, accept complicated inputs, as they are attempting to emulate a web browser. The fact that performance on some inputs can be slower than others is a natural consequence of this. We do not support running them without pre-vetting your inputs to be sure that they will cause acceptable performance for your use case. And as such, we do not recognize it as a security vulnerability if certain inputs trigger longer regular expression execution times.

If you would like to improve performance on certain inputs, a pull request will be accepted. But no security bounties or CEVs will be issued for these performance issues.

You can read more about ReDOS in the article ["ReDOS 'vulnerabilities' and misaligned incentives"](https://blog.yossarian.net/2022/12/28/ReDoS-vulnerabilities-and-misaligned-incentives).
