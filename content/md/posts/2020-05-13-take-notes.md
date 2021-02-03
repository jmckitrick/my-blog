{:title "Take notes"
 :layout :post
}

### Why?

It's been said that 3 qualities of a good programmer are laziness, impatience and hubris.
While this is tongue-in-cheek, it has seeds of truth. Have you ever started working
on a bug or feature and thought 'I'll just keep everything in my head' or 'I'll
remember the important parts as I go'? That's hubris. According to [Debugging
with the Scientific Method](https://youtu.be/FihU5JxmnBg) no matter how smart you think
you are, *write things down*.

So let's start there. How do *you* take notes?


### How to save notes

For years, we saw those ubiquitous black notebooks everywhere. You know the ones,
with the single satin bookmark and the elastic band closure. Pencil and paper is a great
way to brainstorm, and they engage the mind in a way the keyboard does not.

But the notes we are talking about generally aren't brainstorming. We'll talk about that
later. For now, what are some programmer friendly alternatives to pencil and paper?
We generally need media that are easily searchable.

* Plain text

    Yes, there are programmers out there that swear by raw text notes saved in a local folder.

* Local notes app

    Modern operating systems have some kind of note storage app, like Apple Notes.

* Cloud notes app

    There's the Google family of document tools, and specialized tools like Evernote.


### What to save in your notes

What kinds of things should you record? You probably have a ticket system
that specifies the bug or the feature you are working on. And of course, there's the source
code itself. But what notes will *you* take to help you on this item?

* Steps to reproduce a bug

    Often a bug ticket will have the steps to reproduce the bug, but you might find
    more detail is required, or maybe specifics (db ids, etc) that will help you
    track the specific case described.

* Layers of the app you traversed in your exploration

    Many bugs start with an observation of an error at the UI. If you're lucky,
    you'll get steps to reproduce the bug and maybe some logs. You might begin
    the process finding the element in the UI, tracking it to a web page
    or an AJAX call, following that to a back end, maybe all the way to a
    database. Along the way, most modern apps will have several layers
    of framework, both front and back end. The there's the app logic,
    which might have additional layers of its own. Depending on the language
    you are using and the styles it supports, you might even have to deal with
    different coding styles, perhaps including syntax you've not seen elsewhere,
    either because it's very old, very new, or very obscure. And of course,
    you're assuming the code will be well-written and well-commented
    just like *you* would do it, right?

* Third party APIs and libraries

    You might find that your bug takes you to a dead end. Or at least you've gone
    as far with it as you can, and now you have to email tech support for a
    third party API or library. What did you learn that you can record?

Now, your first thought might be that is far too much detail than required
to solve the problem. However, supposed you fix this bug, and move on.
Then, six months later, you're assigned to work on another one. And as you
go through the steps of reproducing it, you have a familiar feeling.

You could go through the entire process again, or you could dig out these notes,
save yourself a lot of trouble, and jump start your memory and bring back all
that context from the first time you worked on the previous bug.
