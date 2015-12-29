---
layout: post
title: "SDL Setup"
category: sdl2
tags: [SDL2, C]
---

So let's start with a quick explanation. I've done some research, and I've
decided I need to commit to some larger project. I picked out my language, C.
The reasons for this are simple: I like low-level, and I was hoping for more
control over what I'm doing. Then I decided on a library. I needed something
cross-platform; that narrowed down my decisions. I also wanted to develop a lot
of the logic myself. You know, as an exercise. After a short trip to Google,
[SDL2](http://www.libsdl.org/) turned out to be the best choice (mobile support
too!).

So that's where I was about a week ago. After a lot of Googling, I've been
using inspiration from [Handmade Hero](https://handmadehero.org/) as to how I
should go about structuring, with my own personal touches.

# Initializing

First things first: make sure to include the library so that we have all of the
functions defined!

{% highlight c %}
#include <SDL2/SDL.h>
{% endhighlight %}

So this was a quick thing to figure out, and I ended up making it it's own
function. The process for initializing an SDL2 window is simple, really.

{% highlight c %}
SDL_Init(SDL_INIT_VIDEO)
{% endhighlight %}

According to the documentation, this returns `0` when successful, or some other
value when failed. running that check we get

{% highlight c %}
if (SDL_Init(SDL_INIT_VIDEO) == 0) {
    // do stuff
}
else {
    printf("error: %s\n", SDL_GetError());
    return -1;
}
{% endhighlight %}

## Window

Now we have to get that pesky window up and on our screen. Replacing our `do
stuff`, we add the following to grab a window from SDL; making sure to destroy
the window after we use it.

{% highlight c %}
SDL_Window *window_p = SDL_CreateWindow(
        "Window Name",
        SDL_WINDOWPOS_CENTERED, SDL_WINDOWPOS_CENTERED,
        800, 600, 0
);

if (window_p != NULL) {
    // do stuff

    SDL_DestroyWindow(window_p);
}
else {
    printf("ERROR: %s\n", SDL_GetError());
}
{% endhighlight %}

## Events

Alright. So we have a window, we have it initialized, now we just have to add
an event loop and we'll be able to see our Window! Events turn out to be
necessary to show the Window, because by processing the events SDL knows to
display the Window in the first place.

Now, looking up the documentation we find

{% highlight c %}
int SDL_PollEvent(SDL_Event *event)
{% endhighlight %}

This populates the event we pass a reference to, and returns a 1 if there was
an event. If there was no event, we get a 0. Conveniently works for a `while`
loop! We also have to keep in mind that we want to continue processing events
until we get an SDL_QUIT Event, which we handle as we see below:

{% highlight c %}
bool done = false;
while (!done) {
    SDL_Event event;
    while (SDL_PollEvent(&event) {
        switch (event.type) {
        // handle our other cases here!
        case SDL_QUIT:
            done = true;
            break;
        default:
            break;
        }
    }
    // do other things
}
{% endhighlight %}

# Weaving Together

Now we have all the pieces necessary for a window to actually show up on our
screen. Tying everything above together, you get something like:

{% highlight c %}
if (SDL_Init(SDL_INIT_VIDEO) == 0) {
    SDL_Window *window_p = SDL_CreateWindow(
            "Window Name",
            SDL_WINDOWPOS_CENTERED, SDL_WINDOWPOS_CENTERED,
            800, 600, 0
    );

    if (window_p != NULL) {
        bool done = false;
        while (!done) {
            SDL_Event event;
            while (SDL_PollEvent(&event) {
                switch (event.type) {
                // handle events here
                case SDL_QUIT:
                    done = true;
                    break;
                default:
                    break;
                }
            }

            // other game code
        }

        SDL_DestroyWindow(window_p);
    }
    else {
        printf("ERROR: %s\n", SDL_GetError());
    }
    SDL_Quit();
    return 0;
}
else {
    printf("ERROR: %s\n", SDL_GetError());
    return -1;
}
{% endhighlight %}
