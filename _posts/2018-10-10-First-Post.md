So I finally managed to open up a Blog on coding.
Now to begin with the design first, I was thinking of adding up a pre-coded theme from the internet.
Now I looked up something called Jekyll, a static site generator. The tutorial on Github said that you have to make
changes to the config.yml file in the main page of the repository. I can't find it though. :/
Maybe the condition is that I have to first setup Jekyll. So let me just find out how to set it up in my PC and Github.

So Jekyll might be the exact thing I'm looking for. It basically converts our input simple text into proper sites using its own CSS and HTML.
This is exactly what I need, since I don't wanna be wasting a lot of time on decorating my blog, and keep formatting codes, snippets and help texts.
I want all of these simply done by the editor.
Now I'm putting in the commands for installation, we'll see how to use it later

> gem install jekyll bundler

 Now since gem isn't installed,

> sudo apt install ruby

 Ruby is installed, Voohoo!
 Now, when I'm trying the former command, the following error popped up:

> ERROR: Failed to build gem native extension.

 Apparently, I need to update the gem version again, and then try. This seems to be a problem of Mac Systems, don't know why I'm facing it!
 I installed the Jekyll and bundler applications, and they are up and running in the git repository.

 Okay, Brilliant! The files have been pushed up into the git repository, and I successfully solved a merge conflict for the first time, yippee!
 I must say, Atom has a brilliant interface for these merge conflicts. Helped a lot.
 Anyway, moving ahead, I now need to actually use jekyll into putting up a nice built up theme.
 This is what the net has to say
       On GitHub, navigate to the main page of the repository.

>      In your repository, browse to config.yml.
      open file editor with edit iconIn the upper-right corner of the file view, click
      to open the file editor.
      Activate the theme by adding a new line to your config.yml with the theme name:

>      Add theme to config fileTo activate one of the officially supported themes, type theme: followed by the name of the theme (as shown in the README in the theme's source repository).
      Add remote theme to config fileTo activate any other open source Jekyll theme hosted on GitHub, type remote_theme: followed by the name of the theme (as shown in the README or other documentation in the theme's source repository).

>      Commit message for your changeAt the bottom of the page, type a short, meaningful commit message that describes the change you made to the file. You can attribute the commit to more than one author in the commit message. For more information, see "Creating a commit with multiple co-authors."

>    Commit branch optionsBelow the commit message fields, decide whether to add your commit to the current branch or to a new branch. If your current branch is master, you should choose to create a new branch for your commit and then create a pull request.

>      Propose file change buttonClick Propose file change.

>      If you created a pull request, merge your pull request into your GitHub Pages publishing branch, which is usually master and sometimes gh-pages.

Now I chose to ignore the new branch thingy, and turns out, it doesn't work. Don't know why, but let's try it with the stupid bramch thing.
Okay, so the world has a lot of idiots, I am probably one of the best ones. I was typing the wrong name for the given theme. I must mention that you always need
to add the theme-name given in the theme's GitHub repo ONLY.

Done! Woohoo! Architect theme is on my repo! I copied their layout code and pasted it in my layouts/default.html
So this is great!
I think I should stop now since I have got a text of Communication Skills tomorrow! :P
