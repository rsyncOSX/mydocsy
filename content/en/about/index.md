---
title: About
linkTitle: About
menu: {main: {weight: 10}}
---

{{% blocks/cover title="About" height="auto" %}}

{{% /blocks/cover %}}

{{% blocks/section color="primary" %}}

Hello,

If you have any ideas or thoughts about RsyncUI, please do not hesitate to contact me at thomeven@gmail.com.

I commenced the development of RsyncOSX in August 2016, which was archived and development ceased after 8 years in August 2024, as a project to learn about Swift development. The devlopment of RsyncUI, which is based upon SwiftUI, commenced in late 2020 and it is in active development.

I hold a master's degree in computing science, but I am not a professional developer. I completed my master's degree during the early 1990s, when Linux was released and the Internet became a public service. A few years prior to that, in 1989, the Web was invented at CERN. There is only one developer involved in the development of RsyncUI, and I am committed to ensuring its stability and user-friendliness. While I am not a UI designer, some users may find the UI complex and less user-friendly.

The maintenance and development of RsyncUI are among my hobbies. If you find RsyncUI useful, I would appreciate it if you could consider giving me a star on the GitHub repository. Each star serves as motivation for me to continue developing RsyncUI. In May 2022, I retired from work at the age of 62. In my spare time, I am a passionate [photographer of birds](https://photosbythomas.netlify.app) and enjoy spending time in the Norwegian mountains. My grandchildren, photography, the development of RsyncUI, and cross-country skiing are some of the activities that keep me occupied.

{.text-center}

{{% /blocks/section %}}

{{% blocks/section color="white" %}}

Although I am an educated IT professional, my professional experience has primarily been as an IT manager rather than a developer.
My coding experience has been limited to private projects such as RsyncUI and RsyncOSX. Google has been an invaluable resource for research and guidance on solving specific problems. Reading about other developers' code and participating in discussions has provided me with valuable insights.

I am continuously learning and adapting to new releases of Swift, SwiftUI, and Xcode, which introduce new features to master. Major changes and updates are documented in the [changelog](/blog/). Additionally, I utilize tools such as [SwiftLint](https://github.com/realm/SwiftLint), [SwiftFormat](https://github.com/nicklockwood/SwiftFormat), and [periphery](https://github.com/peripheryapp/periphery) to enhance my coding practices.

**Why Not the App Store?**

One crucial requirement for macOS applications on the Apple App Store, as outlined by Apple, is:
*"To distribute a macOS app through the Mac App Store, you must enable the App Sandbox capability."*
The App Sandbox imposes certain restrictions on the functionality of an application within its environment. While it is essential for enabling passwordless login via SSH to remote servers, it also causes some limitations with these features when enabled.

{.text-center}

{{% /blocks/section %}}

{{% blocks/section color="primary" %}}

**How are these pages constructed?**

Hugo, a static site generator, serves as the web framework responsible for constructing these pages. The source code for this website is hosted on GitHub.
Netlify, the web server, automatically detects changes made to the main branch and promptly rebuilds the server.
The Hugo theme utilized is [docsy](https://github.com/google/docsy), another open-source project hosted on GitHub.
Upon making modifications or additions to pages, I commit these changes to GitHub, and Netlify promptly constructs the new server within seconds.

{.text-center}

{{% /blocks/section %}}
