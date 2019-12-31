---
title: "Avoid data loss"
weight: 1
---

## Misfiling risk

The main risk of using Treefactor is that the user misfiles something - a file under the wrong directory, a heading under the wrong parent, a line under the wrong heading. Further actions taken on the parent object may worsen the situation. For example, one might decide that the parent object is obsolete, and delete it without inspecting its contents.

Treefactor is not terribly complicated, but one should be familiar with Dired and especially outline manipulation before using it in production. It is meant for users who want to go fast and skip manual steps. These are arguably things beginners shouldn't do.

## Files first, then outlines

Using Treefactor for outline manipulation currently has somewhat more potential for novice user error than existing Org commands. However, one of the reasons I developed Treefactor was because even as an experienced user I easily become confused when manipulating deep complex outlines, and made misfiling mistakes that resulted in frustration and data loss.

When throwing files and directories in Dired, Treefactor has somewhat less potential for user error than Dired's native commands. Dired is powerful and complex, and it's possible to make mistakes while quickly issuing repetitive commands. Treefactor automates and simplifies the most common refile operation, reducing the potential for human error. Because Treefactor logs file destinations and puts them in a separate 0-Inbox directory, mistakes are easily recoverable. The same isn't always true in native Dired.

I recommend that beginners learn Treefactor by learning its Dired side first, by sorting files and directories. When comfortable with the process, then try outline manipulation.

When manipulating outlines, always use a Git repo. Magit makes this easy.

Autosave is a less reliable solution when filenames, paths and content are in flux due to Treefactor sorting. Don't rely on it.

**Important**: Read the "Inbox.org template - keep transit heading level consistent!" section on the [Customization](Customization.html) page. It explains how to avoid accidentally misfiling headings under unrelated parents. Step-parents can be cruel!

## Recovery

Wondering where something went? A message appears in the minibuffer displaying the destination of text and files moved with treefactor-throw and treefactor-up. The log is in the *Messages* buffer.

treefactor-throw and treefactor-up automatically save changes to text files. I suggest giving Emacs' undo history generous settings to permit unwinding mistakes.

The last text thrown is saved in the variable treefactor-object-text until the Emacs session ends. Thrown text is not saved to the kill ring, as this interferes with user yank commands and overcrowds the kill ring.

## Bugs

Treefactor's search for "Inbox.org" or "0-Inbox/" is case sensitive. Lower case "i" will not match. Linux will simply ignore a non-match. However, MacOS doesn't distinguish case. This causes the treefactor-throw operation to fail with an error. No user data is altered. The solution is simply to capitalize the "i".
