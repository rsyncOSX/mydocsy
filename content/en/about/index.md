---
title: About
linkTitle: About
menu: {main: {weight: 10}}
---

{{% blocks/cover title="About" %}}

{{% /blocks/cover %}}

{{% blocks/section %}}



Hi, I am Thomas, e-mail: <thomeven@gmail.com>, the developer of RsyncUI (and RsyncOSX which was archived and not maintained August 2024). The development of RsyncOSX commenced early in 2016 as a personal project to learn Swift. And the development of RsyncUI began late in 2020 to learn SwiftUI. I have a master's degree in computing science, but I am not a *professional developer*. I did my master's in the days when Linux was released in 1991 and the Internet became a public service. And a few years ahead of that, in 1989, the Web was invented at Cern.

There is one developer only, me, and I am doing what I can to keep RsyncUI as stable and user-friendly as possible. I am not a UI designer, and some users might find the UI complicated and less user-friendly. The maintenance and development of RsyncUI is one of my hobbies. If you like using RsyncUI, please consider giving me a star on the GitHub repository. Every single star is motivation for me to continue developing and keeping the apps updated for the latest version of macOS.

In May 2022, I retired from work at the age of 62. I am [a passionate photographer](https://photosbythomas.netlify.app/) of birds and love staying in the Norwegian mountains. Grandkids, photography, continuing maintenance of my macOS applications, and cross-country skiing are keeping me busy.

{.text-center}

{{% /blocks/section %}}

{{% blocks/section %}}

## A few words about the code

Even though I am an educated IT person, most of my professional work has been as an IT manager and not a developer. Most of my coding experience is with private projects such as RsyncUI and RsyncOSX. Google is and has been a great resource for research and advice on how to solve specific problems. Reading about other developers code and discussions are always valuable input for me.

I am learning almost every day and by every new release of Swift, SwiftUI and Xcode there are new features to learn. Any major changes and updates are most likely updated in the [changelog](/post/changelog/). I am also using tools like [SwiftLint](https://github.com/realm/SwiftLint), [SwiftFormat](https://github.com/nicklockwood/SwiftFormat) and [periphery](https://github.com/peripheryapp/periphery) to assist me in writing code.

## No right or wrong

I also believe there is no right or wrong in development. Each developer and team chooses their way to develop based on their skills and what they want to achieve. I know my own code, and I have no issues understanding what my code is doing. And as times go on, in my opinion, I make changes to the code for the better. I also fully understand that other developers might have some issues understanding my code. 

What I also experience is how my own understanding of OO, declarative programming, Swift and SwiftUI is growing. I would not write code today as I did when I commenced my project in 2015 to learn Swift. But still, I am not a professional programmer, and there are several topics within Swift and SwiftUI that I do not understand. But I am capable of learning; if I spend enough time on a topic, there is a good probability that I will get the idea.


{.text-center}

{{% /blocks/section %}}

{{% blocks/section %}}

## Why not App Store

One important requirement for macOS apps on Apple App Store is quote Apple: *"To distribute a macOS app through the Mac App Store, you must enable the App Sandbox capability."* There are restrictions what an app can do inside the App Sandbox. Execute `rsync`, obvious, and enable passwordless login by ssh to remote servers are two must have features. The Apple Sandbox causes a few issues to both features when switch on. And I have not yet any success when RsyncUI is set to use default rsync in macOS and only attached discs. But I am inveastigating, so there might be an Apple App Store version in the future.


## How are these pages built?

Hugo, which is a static site generator, is the web framework serving these pages. The source for this website is hosted on GitHub. Netlify, which runs the web server, automatically picks up changes on the main branch and rebuilds the server. The Hugo theme used is another open-source project hosted on GitHub.

Every time I change or add pages, I commit the changes to GitHub, and Netlify automatically builds the new server in seconds.

{.text-center}

{{% /blocks/section %}}