---
title: Defold engine and editor FAQ
brief: Frequently asked questions about the Defold game engine, editor and platform.
---

# Frequently asked questions

## General questions

Is Defold really free?
: Yes, the Defold engine and editor with full functionality is completely free of charge. No hidden costs, fees or royalties. Just free. And we will not start to charge for anything after the beta period.

Why on earth would King give Defold away?
: This may seem out of the ordinary, that a commercial game company releases its core technology for free, but here’s how we see it: the more people who use Defold, the better the engine will be. By releasing Defold to the community, _everyone_​ can help making Defold better, by creating tutorials, by finding bugs, improving the documentation, and much more. And since King uses Defold internally, every day – the better the engine gets, the happier our internal developers will be. We believe great tech attracts great talent. All in all, we believe this ultimately leads to better games – not only for us at King, but for all game developers.

  That’s it. And that’s what we’re all about – making and celebrating great games and the amazing people creating them.

How long will you support Defold?
: We are deeply committed to Defold. Teams at King game studios all over the world are creating games made with Defold and have been doing it for years. It is not going away.

Can I trust Defold for professional development?
: Yes, we believe in "eating your own dogfood" and use it ourselves at King to develop almost all of our new game IP:s.

Why do I have to store my games on Defold's servers?
: Starting with Defold editor 2 you can store your games wherever you want. Defold was originally designed to be a complete turnkey service, including collaboration tools and storage. There are benefits to using our servers and we will continue to supply value to those who do use it through the dashboard. However, we realize that some users prefer other storage providers and we are working on supporting that.

  If you are tech-savvy, there is a workaround available. See https://forum.defold.com/t/howto-alternative-project-hosting/1309[this HOWTO on our forum].

Who made Defold?
: Defold was created by Ragnar Svensson and Christian Murray. They started working on the engine, editor and servers in 2009. King and Defold started a partnership in 2013 and King acquired Defold in 2014. Read the full story [here](/about-us).

## Platform questions

What platforms does Defold run on?
: The following platforms are supported for the editor/tools and the engine runtime:

  | System                    | Supported            |
  | ------------------------- | -------------------- |
  | macOS/OS X 10.7 Lion      | Editor and runtime   |
  | Windows Vista             | Editor and runtime   |
  | Linux (32 bit and 64 bit) | Editor and runtime   |
  | iOS 5.1                   | Runtime              |
  | Android 2.3 (API level 9) | Runtime              |
  | HTML5                     | Runtime              |

What target platforms can I develop games for with Defold?
: With one click you can publish to iOS, Android and HTML5 as well as macOS/OS X, Windows and Linux. It’s truly one codebase, six supported platforms.

What rendering API does Defold rely on?
: Defold uses OpenGL ES 2.0 for graphics rendering, which is available on all our supported
platforms.

Can I do 3D games in Defold?
: Absolutely! The engine is a full blown 3D engine. However, the toolset is made for 2D so you will have to do a lot of heavy lifting yourself. Better 3D support is planned.

What programming language do I work with in Defold?
: All application and game logic in your Defold project is controlled through script. The Defold engine has the Lua language embedded for scripting. Lua is a lightweight dynamic language that is fast and very powerful. Read more on our [technology summary](/technology).

  When building custom materials, OpenGL ES SL shader language is used to write vertex and fragment
shaders.

Is there a way to know what version I'm running?
: Yes, select the "About Defold Editor" in the menu. The popup clearly shows Defold beta version and, more importantly, the specific release SHA1. For runtime version lookup, use [`sys.get_engine_info()`](/ref/sys/#sys.get_engine_info).

  The latest beta version available for download from http://d.defold.com/beta can be checked by opening http://d.defold.com/beta/info.json (the same file exists for stable versions as well: http://d.defold.com/stable/info.json)

Are Defold beta versions auto-updating?
: Yes. The Defold beta checks for an update at startup, just like the Defold stable version does.

<a name="external-git-tools"></a>

Can I use external Git tools?
: Yes you can:
  1. Check out a project for the first time via Open Project and New Branch
  2. Add the local repository found in "Defold/branches/[project_id]/[user_id]/[name_of_branch]" to your Git client.
  3. Specify your Defold username. The password is the "Access token" that you find under "Settings" in the Defold Dashboard (the huge hexadecimal number).
  4. You can now add, commit, revert, branch and merge as much as you want. Any changes are immediately reflected in Defold. Note that Defold automatically stages all changes that you make in the editor.

I try to publish my game to Appstore. How should I respond to IDFA?
: Defold has built in support for IDFA (Advertising Identifier). You can fetch it via `sys.get_sys_info()`. When submitting, Apple has three checkboxes for their three valid use cases for the IDFA:

  1. Serve ads within the app
  2. Install attribution from ads
  3. User action attribution from ads

  If you check option 1, the app reviewer will look for ads to show up in the app. If your game does not show ads, the game might get rejected. Defold uses the id for cross promotion of your games, so you should check option 2.

## Errors using Defold

Why doesn't the editor start or open my project?
: Check if there are spaces in the path leading up to the Defold application. For instance, if you put the folder *Defold-macosx* containing the OSX version of the editor in your *Applications* folder, then you should be ok.  If you rename the folder *Defold macosx* the editor might not start anymore. On Windows, putting Defold under *C:\\Program Files\\* can trigger this problem. This is due to a known bug in the underlying Eclipse framework.

I can't start the game and there is no build error. What's wrong?
: The build process can fail to rebuild files in rare cases where it have
  previously encountered build errors that you have fixed. Force a full rebuild
  by selecting *Project > Rebuild And Launch* from the menu.

Why does my HTML5-app freeze at the splash screen in Chrome?
: In some cases it is not possible to run a game in the browser locally
  from the filesystem. Running from the editor serves the game from a local
  webserver. You can, for instance, use SimpleHTTPServer in Python:

  ```sh
  $ python -m SimpleHTTPServer [port]
  ```

## Linux problems

I'm running on Linux 64 bit and the editor won't start.
: Make sure you downloaded the 64 bit version of the editor from the dashboard and that you start the editor with the supplied shell script:

  ```sh
  $ ./Defold-linux.sh
  ```

  Do *not* execute *Defold* directly.

I'm running on Linux and nothing happens when I try to open my projects.
: If you are running a 32 bit Linux, your installation may lack a compatible libwebkitgtk. Install *libwebkitgtk version 1.0-0* and restart the editor.

I can't create a new branch for my project on Linux.
: Make sure that you have *libssl 0.9.8* installed on your machine. Some distributions come with a later version, but Defold needs version *0.9.8*.

When I try to run my game on Linux, the engine doesn't start.
: Check the console output in the editor. If you get the following message:

  ```
  /home/myname/Desktop/Defold/plugins/com.dynamo.cr.engine_1.0.0.201502231306/engine/linux/dmengine: error while loading shared libraries: libopenal.so.1: cannot open shared object file: No such file or directory
  ```

  then you need to install *libopenal1*.

## Working with game content

Does Defold support prefabs?
: Yes, it does. They are called collections. They allow you to create complex game object
  hierarchies and store those as a separate building blocks that you can instance in the
  editor or at runtime (through collection spawning). For GUI nodes there is support for GUI templates.

I can't add a game object as a child to another game object, why?
: Chances are that you try to add a child in the game object file and that is not possible.
  To understand why you have to remember that parent-child hierarchies are strictly a _scene-graph_
  transform hierarchy. A game object that has not been placed (or spawned) into a scene (collection) is not part of a scene-graph and can't therefore be part of a scene-graph hierarchy.

Why can't I broadcast messages to all children of a game object?
: Parent-child relations express nothing else than the scene-graph transform relations 
  and should not be mistaken for object orientation aggregates. If you try to focus on your game data and how to best transform it as your game alter its state you will likely find less need to send messages with state data to many objects all the time. In the cases where you will need data hierarchies, these are easily constructed and handled in Lua.

Why am I experiencing visual artifacts around the edges of my sprites?
: That is a visual artifact called "edge bleeding" where the edge pixels of neighbouring
  pixels in an atlas bleed into the image assigned to your sprite. The solution is to pad
  the edge of your atlas images with extra row(s) and column(s) of identical pixels.
  Luckily this can be done automatically by the atlas editor in Defold.
  Open your atlas and set the *Extrude Borders* value to 1.

Can I tint my sprites easily, or do I have to write my own shader for it?
: Yes, you can. The built-in sprite shader has a constant "tint" defined:

  ```lua
  sprite.set_constant("#sprite", "tint", vmath.vector4(r, g, b, a))
  ```

If I set the z coordinate of a sprite to 100 then it's not rendered. Why?
: The Z-position of a game object controls rendering order. Low values are drawn before
  higher values. In the default render script game objects with a depth ranging between -1 and 1
  are drawn, anything lower or higher will not be drawn. You can read more about the
  rendering script in the official [Rendering documentation](/manuals/rendering).
  On GUI nodes the Z value is ignored and does not affect rendering order at all.
  Instead nodes are rendered in the order they are listed and according to child hierarchies
  (and layering). Read more about gui rendering and draw call optimization using layers
  in the official [GUI documentation](/manuals/gui).

Would changing the view projection Z-range to -100 to 100 impact performance?
: No. The only effect is precision. The z-buffer is logarithmic and have very fine
  resolution of z values close to 0 and less resolution far away from 0.
  For instance, with a 24 bit buffer the values 10.0 and 10.000005 can be differentiated
  whereas 10000 and 10005 cannot.

There is no consistency to how angles are represented, why?
: There is actually consistency. Angles are expressed as degrees everywhere
  in the editor and the game API:s. The math libs use radians. Currently the
  convention breaks for the `angular_velocity` physics property that is
  currently expressed as radians/s. That is expected to change.

When creating a GUI box-node with only color (no texture), how will it be rendered?
: It is just a vertex colored shape. Bear in mind that it will still cost fill-rate.

If I change assets on the fly, will the engine automatically unload them?
: All resources are ref-counted internally. As soon as the ref-count is zero the resource
  is released.

Is it possible to play audio without the use of an audio component attached to a game object?
: Everything is component-based. It's possible to create a headless
  gameobject with multiple sounds and play sounds by sending messages to the
  sound-controller object. A benefit is that you can duck sounds based on
  interval, etc

Is it possible to change the audio file associated with an audio component at run time?
: In general all resources are statically declared with the benefit that
  you get resource management for free.

Is there a way to access the physics collision shape properties?
: No, it is currently not possible.

Is there any quick way to render the collision objects in my scene? (like Box2D's debugdraw)
: Yes, set *physics.debug* flag in game.project.
  (Refer to the official [Project settings documentation](/manuals/project-settings))

What are the performance costs of having many contacts/collisions?
: Defold runs a modified version of Box2D in the background and the performance cost
  should be quite similar. You can always see how much time the engine spends on physics
  by bringing up the [profiler](/manuals/debugging).
  You should also consider what kind of collisions objects you use. Static objects are
  cheaper performance wise for instance. Refer to the official [Physics
  documentation](/manuals/physics) in Defold for more details.

What's the performance impact of having many ParticleFx components?
: It depends on if they are playing or not. A ParticleFx that isn't playing have zero performance cost. The performance implication of a playing ParticleFx must be evaluated using the profiler since it's impact depends on how it is configured. The memory cost of a ParticleFX is around 140 bytes. As with most other things the memory is allocated up front for the number of ParticleFx defined as max_count in game.project.

How do I receive input to a game object inside a collection loaded via a collection proxy?
: Each proxy loaded collection has their own input stack. Input is routed from the main collection input stack via the proxy component to the objects in the collection. This means that it's not enough for the game object in the loaded collection to acquire input focus, the game object that _holds_ the proxy component need to acquire input focus as well. See the [Input documentation](/manuals/input) for details.

Is there a way to know what platform the game is running on at runtime?
: Yes, check out [`sys.get_sys_info()`](/ref/sys#sys.get_sys_info).

Can I use string type script properties?
: No. Defold supports properties of [hash](/ref/builtins#hash) types. These can be used
  to indicate types, state identifiers or keys of any kind. Hashes can also be used to store
  game object id:s (paths) although [url](/ref/msg#msg.url) properties are often
  preferrable since the editor automatically populate a drop-down with relevant url:s
  for you. See the [Script properties documentation](/manuals/script-properties) for details.

## Lua

Which Lua standard libraries are included in Defold?
: Defold includes all of the [Lua 5.1 standard libraries](http://www.lua.org/manual/5.1/manual.html#5) as well as a socket and a bit operation library:
  - base (`assert()`, `error()`, `print()`, `ipairs()`, `require()` etc)
  - coroutine
  - package
  - string
  - table
  - math
  - io
  - os
  - debug
  - socket (from [LuaSocket](https://github.com/diegonehab/luasocket))
  - bitop (from [BitOp](http://bitop.luajit.org/api.html))

  All libraries are documented in the [reference API documentation](/ref/)

## The forum

Can I post a thread where I advertise my work?
: Of course! We have a special "Work for hire" category for that. We will always encourage everything which benefits the community, and offering your services to the community---for remuneration or not---is a good example of that.

I made a thread and added my work—can I add more?
: In order to reduce bumping of "Work for hire" threads, you may not post more than once per 14 days in your own thread (unless it’s a direct reply to a comment in the thread, in which case you may reply). If you want to add additional work to your thread within the 14-day period, you must edit your existing posts with your added content.

Can I use the Work for Hire category to post job offerings?
: Sure, knock yourselves out! It can be used for offerings as well as requests, e.g. “Programmer looking for 2D pixel artist; I’m rich and I’ll pay you well”.
