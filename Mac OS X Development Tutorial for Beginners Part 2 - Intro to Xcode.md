# macOS X 初学者开发教程 第二部分 OS X App剖析

#### [原文地址](https://www.raywenderlich.com/110267/mac-os-x-development-tutorial-beginners-part-2-os-x-app-anatomy) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <p>
        <img class="alignright size-full wp-image-110249 bordered" src="https://koenig-media.raywenderlich.com/uploads/2015/07/250x250.png"
        alt="250x250" width="250" height="250" srcset="https://koenig-media.raywenderlich.com/uploads/2015/07/250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2015/07/250x250-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2015/07/250x250-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2015/07/250x250-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2015/07/250x250-128x128.png 128w"
        sizes="(max-width: 250px) 100vw, 250px">
    </p>
    <p>
        Welcome back to our 3-part Mac OS X Development tutorial for beginner
        series!
    </p>
    <ol>
        <li>
            In
            <a href="http://www.raywenderlich.com/110170/mac-os-x-development-tutorial-for-beginners-part-1-intro-to-xcode"
            sl-processed="1">
                part 1
            </a>
            you first learned&nbsp;how to obtain the tools you need to develop for
            OS X. Then, using an app you downloaded as an example, you took a tour
            of Xcode, discovering how to run an app, edit code, design the UI and debug
            it.
        </li>
        <li>
            In this second part, you’ll take a step back from Xcode to learn about
            the components that make up an OS X app. From how an app starts, through
            how the UI is constructed all the way to handling user interaction.
        </li>
        <li>
            You’ll get your hands dirty in the
            <a href="http://www.raywenderlich.com/110269/mac-os-x-development-tutorial-for-beginners-part-3-your-first-os-x-app"
            sl-processed="1">
                final part
            </a>
            – building your first ever OS X app. Starting from nothing, you’ll soon
            have a simple app up and running on your mac!
        </li>
    </ol>
    <p>
        This article&nbsp;is aimed at developers who&nbsp;have either completed
        <a href="http://www.raywenderlich.com/110170/mac-os-x-development-tutorial-for-beginners-part-1-intro-to-xcode"
        sl-processed="1">
            part one
        </a>
        of the series, or have experience with Xcode. It assumes little or no
        knowledge of OS X apps, and if you’re already familiar with the architecture
        of OS X apps, you might like to skim through before skipping right on to
        the
        <a href="http://www.raywenderlich.com/110269/mac-os-x-development-tutorial-for-beginners-part-3-your-first-os-x-app"
        sl-processed="1">
            final part
        </a>
        .
    </p>
    <p>
        By the end of this article you’ll have a good grounding in how the different
        parts of an OS X app fit together, although not necessarily a wide-ranging
        understanding of how each of them works.
    </p>
    <div class="note">
        <p>
            <em>
                Note:
            </em>
            This part of the series is just background information that you need to
            know about how OS X apps work; there is no coding involved.
        </p>
        <p>
            Just sit back, relax, and learn – you’ll get back to coding and make your
            first OS X app in the next and final part of the series!
        </p>
    </div>
    <h2>
        How Does an OS X App Start?
    </h2>
    <p>
        Your journey through an OS X app starts right at the beginning – looking
        at how an app actually
        <i>
            starts
        </i>
        .
    </p>
    <p>
        There are three components that you need to be aware of when considering
        the OS X app start process:
    </p>
    <ul>
        <li>
            <em>
                App Delegate
            </em>
            : The entry point for code. The App Delegate provides methods associated
            with both the lifecycle of the app, and its interaction with the operating
            system. This is your first opportunity to run code, and provides you with
            notifications from OS X, such as Handoff requests, command line arguments
            and push notifications.
        </li>
        <li>
            <em>
                Storyboard
            </em>
            : Storyboards have a designated “entry point”, and this allows the system
            to construct the UI at app launch. The entrypoint looks like an arrow on
            the left hand side of a scene:
            <br>
            <img class="aligncenter size-full wp-image-111915" src="https://koenig-media.raywenderlich.com/uploads/2015/08/storyboard_entry.png"
            alt="storyboard_entry" width="264" height="164">
            <br>
            This denotes which of the scenes in the storyboard will form the initial
            UI of your app.
        </li>
        <li>
            <em>
                Info.plist
            </em>
            : You can have multiple storyboards within your app, so how does OS X
            know which one it should use as the initial UI? This information (and a
            load of other useful things) is stored inside the
            <em>
                Info.plist
            </em>
            file. You can see the relevant entry below:
            <img class="aligncenter size-medium wp-image-111908" src="https://koenig-media.raywenderlich.com/uploads/2015/08/info_plist-480x245.png"
            alt="info_plist" width="480" height="245" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/info_plist-480x245.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/08/info_plist-700x357.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/08/info_plist.png 1238w"
            sizes="(max-width: 480px) 100vw, 480px">
            <p>
                This file contains lots of useful app configuration options, many of which
                are exposed through the target configuration screen in Xcode. The image
                below shows the same storyboard setting in a more user-friendly location:
            </p>
            <p>
                <img class="aligncenter wp-image-111912 size-large" src="https://koenig-media.raywenderlich.com/uploads/2015/08/project_config-700x436.png"
                alt="project_config" width="700" height="436" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/project_config-700x436.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/08/project_config-480x299.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/08/project_config.png 1448w"
                sizes="(max-width: 700px) 100vw, 700px">
            </p>
        </li>
    </ul>
    <p>
        Starting an app is
        <i>
            slightly
        </i>
        more complicated than this, but these three places explain where you can
        interact and configure your app’s startup. Now that you’ve got your app
        up and running it’s time to take a look at a very important aspect – its
        User Interface.
    </p>
    <h2>
        User interface
    </h2>
    <p>
        You’re already aware of the fact that the UI can be provided by a storyboard,
        but what does this actually mean? In this section you’ll cover the different
        UI components – what they represent and how they fit together.
    </p>
    <p>
        <img class="aligncenter size-large wp-image-111919" src="https://koenig-media.raywenderlich.com/uploads/2015/08/app_components-632x500.png"
        alt="app_components" width="632" height="500" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/app_components-632x500.png 632w, https://koenig-media.raywenderlich.com/uploads/2015/08/app_components-405x320.png 405w, https://koenig-media.raywenderlich.com/uploads/2015/08/app_components.png 1442w"
        sizes="(max-width: 632px) 100vw, 632px">
    </p>
    <h3>
        Window
    </h3>
    <p>
        The UI for your app will be contained within one or more window objects.
        These represent an area of the screen for which your app is responsible
        for providing the UI. The operating system runs a window manager that handles
        the moving and resizing of these windows, updating your app as the user
        makes these changes.
    </p>
    <p>
        In addition to representing the visualization of your app, the window
        object also handles passing user events triggered by user interaction with
        the mouse and keyboard into your app.
    </p>
    <p>
        Although you can interact directly with a window object, often they’re
        managed by window controllers – especially when used in conjunction with
        storyboards.
    </p>
    <p>
        A window controller is responsible for the loading of the window itself,
        and allows you to hook into different events throughout the lifecycle of
        the window.
    </p>
    <p>
        A storyboard would contain at least one window controller, which is represented
        as follows:
    </p>
    <p>
        <img class="aligncenter wp-image-111918 size-medium" src="https://koenig-media.raywenderlich.com/uploads/2015/08/window_controller-475x320.png"
        alt="window_controller" width="475" height="320" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/window_controller-475x320.png 475w, https://koenig-media.raywenderlich.com/uploads/2015/08/window_controller-700x471.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/08/window_controller.png 1078w"
        sizes="(max-width: 475px) 100vw, 475px">
    </p>
    <p>
        Window controllers are represented by the
        <code>
            NSWindowController
        </code>
        class, and as you configure your different windows, you would normally
        create different subclasses to manage their individual behavior.
    </p>
    <h3>
        Views
    </h3>
    <p>
        The window specifies the area of the screen that your app is responsible
        for drawing on, but not what to draw. This is one of the primary responsibilities
        of the view – providing you with functionality to draw on the screen.
    </p>
    <p>
        Views are rectangular in shape, and are represented by the
        <code>
            NSView
        </code>
        class. Views exist within a hierarchy – i.e. any view can contain zero
        or more subviews – allowing you to construct a complex layout using much
        simpler, reusable view components.
    </p>
    <h3>
        View Controllers
    </h3>
    <p>
        In the same way that windows are managed by a window controller in storyboards,
        views are managed by a view controller class. This links the view hierarchy
        in with the the model layer, either by manipulating properties directly,
        or through Cocoa bindings.
    </p>
    <p>
        In a typical application, a view controller is a reusable component that,
        when provided a model object of a particular type, would update all of
        its constituent views to represent the values of its associated model object.
    </p>
    <p>
        For example, in the previous tutorial you poked around the
        <em>
            HubEvent
        </em>
        app.
    </p>
    <p>
        <img class="aligncenter wp-image-111920 size-medium" src="https://koenig-media.raywenderlich.com/uploads/2015/08/view_controllers-480x311.png"
        alt="view_controllers" width="480" height="311" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/view_controllers-480x311.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/08/view_controllers-700x453.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/08/view_controllers.png 1232w"
        sizes="(max-width: 480px) 100vw, 480px">
    </p>
    <p>
        In the above screenshot, you can see that it is made up of two major view
        controllers – one managing the table view on the top, and the other the
        detail text view. When you select a row in the table view, it sets the
        model object on the lower detail view controller, which then updates the
        text view to display the correct JSON.
    </p>
    <p>
        View controllers are represented by
        <code>
            NSViewController
        </code>
        , which provides a full range of lifecycle events – allowing you to perform
        custom actions at different times. For example you can fire animation as
        the view is about to appear on the screen with
        <code>
            viewWillAppear()
        </code>
        , or populate relevant views with data once the view hierarchy has correctly
        loaded with
        <code>
            viewDidLoad()
        </code>
        .
    </p>
    <p>
        Your app is likely to be formed from a selection of custom subclasses
        of
        <code>
            NSViewController
        </code>
        , each responsible for a different section of a window. They’re an incredibly
        important aspect of an app – forming the link that allows you to display
        the underlying data to the user.
    </p>
    <h3>
        View components
    </h3>
    <p>
        You’ve discovered that views are used to draw on the screen – but how
        is that actually achieved? At the lowest level you can create a custom
        subclass of
        <code>
            NSView
        </code>
        and override the
        <code>
            drawRect()
        </code>
        method to manually draw the content of your view.
    </p>
    <p>
        This is extremely powerful – allowing you to create completely custom
        views, but would be arduous if you had to do this to draw some text on
        the screen!
    </p>
    <p>
        Luckily, you don’t have to. AppKit contains a large selection of commonly
        used
        <code>
            NSView
        </code>
        subclasses that you can use to display content on the screen.
    </p>
    <p>
        Some of the most useful examples are:
    </p>
    <ul>
        <li>
            <em>
                Label
            </em>
            : Displays static text. Configurable font and appearance
            <br>
            <img class="aligncenter wp-image-111909 size-full" src="https://koenig-media.raywenderlich.com/uploads/2015/08/label.png"
            alt="" width="430" height="120">
        </li>
        <li>
            <em>
                Text Field
            </em>
            : User-editable text control. Used to collect a string from the user.
            <br>
            <img class="aligncenter size-full wp-image-111917" src="https://koenig-media.raywenderlich.com/uploads/2015/08/text_field.png"
            alt="text_field" width="474" height="110">
        </li>
        <li>
            <em>
                Image View
            </em>
            : Draws an image – provided by an
            <code>
                NSImage
            </code>
            object.
            <br>
            <img class="aligncenter size-full wp-image-111907" src="https://koenig-media.raywenderlich.com/uploads/2015/08/image_view.png"
            alt="image_view" width="468" height="108">
        </li>
        <li>
            <em>
                Push Button
            </em>
            : One of the many button types – each of which respond to a user’s mouse
            click.
            <br>
            <img class="aligncenter size-full wp-image-111913" src="https://koenig-media.raywenderlich.com/uploads/2015/08/push_button.png"
            alt="push_button" width="470" height="88">
        </li>
        <li>
            <em>
                Table View
            </em>
            : An example of one of the many view subclasses used for showing not just
            <i>
                one
            </i>
            data object, but rather a collection of them.
            <br>
            <img class="aligncenter size-full wp-image-111916" src="https://koenig-media.raywenderlich.com/uploads/2015/08/table_view.png"
            alt="table_view" width="490" height="112" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/table_view.png 490w, https://koenig-media.raywenderlich.com/uploads/2015/08/table_view-480x110.png 480w"
            sizes="(max-width: 490px) 100vw, 490px">
        </li>
    </ul>
    <p>
        These are just a few of the different view subclasses available to you
        as you build up the user interface of your app. You can discover the entire
        range in the object library within Interface Builder:
    </p>
    <p>
        <img class="aligncenter size-large wp-image-111911" src="https://koenig-media.raywenderlich.com/uploads/2015/08/object_library-383x500.png"
        alt="object_library" width="383" height="500" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/object_library-383x500.png 383w, https://koenig-media.raywenderlich.com/uploads/2015/08/object_library-245x320.png 245w, https://koenig-media.raywenderlich.com/uploads/2015/08/object_library.png 522w"
        sizes="(max-width: 383px) 100vw, 383px">
    </p>
    <p>
        The raywenderlich.com OS X tutorial team will also be putting together
        a quick reference guide to different UI components over the coming months
        – so be sure to check back for that.
    </p>
    <h3>
        Viewing collections
    </h3>
    <p>
        Often you’ll want your app to display UI for multiple model objects at
        the same time – for example showing a list of upcoming appointments, or
        a set of photos in an album.
    </p>
    <p>
        OS X provides two different views that are designed to show collections
        of model objects – in the form of table views and collection views.
    </p>
    <p>
        As their name suggests, table views are used to show tabular data, with
        rows representing individual model objects, and the columns representing
        attributes on those objects.
    </p>
    <p>
        <img class="aligncenter size-medium wp-image-111922" src="https://koenig-media.raywenderlich.com/uploads/2015/08/table_view_sample-480x145.png"
        alt="table_view_sample" width="480" height="145" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/table_view_sample-480x145.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/08/table_view_sample-700x212.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/08/table_view_sample.png 1220w"
        sizes="(max-width: 480px) 100vw, 480px">
    </p>
    <p>
        Table views are made up of cells that can be recycled as they scroll on
        and off screen. Data can be provided either via a data source protocol
        or using Cocoa Bindings.
    </p>
    <p>
        Tables support sorting, editing and custom cells, giving you a very powerful
        view for displaying data.
    </p>
    <p>
        The more generic collection view is also comprised of a collection of
        cells, but this time, each cell represents the entire model object. The
        layout of these cells is completely customizable.
    </p>
    <p>
        <img class="aligncenter size-medium wp-image-111902" src="https://koenig-media.raywenderlich.com/uploads/2015/08/collection_view-475x320.png"
        alt="collection_view" width="475" height="320" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/collection_view-475x320.png 475w, https://koenig-media.raywenderlich.com/uploads/2015/08/collection_view-700x472.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/08/collection_view.png 1314w"
        sizes="(max-width: 475px) 100vw, 475px">
        <img class="aligncenter wp-image-111903 size-medium" src="https://koenig-media.raywenderlich.com/uploads/2015/08/collection_view_circle-480x308.png"
        alt="collection_view_circle" width="480" height="308" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/collection_view_circle-480x308.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/08/collection_view_circle-700x449.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/08/collection_view_circle.png 1234w"
        sizes="(max-width: 480px) 100vw, 480px">
    </p>
    <p>
        Similarly to the table view, the data for a collection view can be provided
        either via a data source protocol, or through Cocoa Bindings. Cells are
        also recycled as they disappear out of the view, reducing the memory footprint.
    </p>
    <p>
        Collection views have built in support for cell selection, animated re-ordering
        and grouping cells into sections.
    </p>
    <h3>
        Handling user interaction
    </h3>
    <p>
        A key part of any OS X is allowing user interaction through the mouse,
        trackpad, keyboard and any other of a number of input devices. To assist
        with designing user input to your app, OS X provides a unified event dispatch
        model, built around the concept of a responder chain.
    </p>
    <p>
        Events generated from a keyboard are known as
        <em>
            Key Events
        </em>
        , and these follow quite a complicated path to arrive at your app. Some
        key presses don’t event make it to your app – as they are intercepted at
        the OS level (e.g. power button, screen brightness, volume).
    </p>
    <p>
        Key events can represents a single key, or a key combination – and when
        they arrive at your app, they are first checked to see whether they are
        a keyboard shortcut that’s bound to a menu item.
    </p>
    <p>
        If not, they are checked to see whether the are used to navigate around
        the user interface of your app – e.g. tabbing between input fields. If
        this isn’t the case, then the window works out which of its views is currently
        “active” (so-called first responder) before passing it the key events.
        These can either be interpreted as per-view commands or as characters to
        insert.
    </p>
    <p>
        Keyboard input is really quite complicated, since it can affect many levels
        of the system and app architecture, but OS X goes a long way to assist
        with this processing. In many cases, you’ll find that it behaves as you
        would expect it out of the box.
    </p>
    <p>
        Mouse-like events are passed to your application, which establishes which
        window and hence view they were performed on, before passing them to your
        custom subclass to allow you to handle them appropriately. The responder
        class (which views inherit from) includes methods you can override which
        get called when a clicks and moves the mouse.
    </p>
    <p>
        Trackpads offer lots of additional gestures to a traditional mouse, so
        the concept of gesture recognizers has been borrowed from iOS. These can
        be use to interpret a sequence of multi-finger touches into a semantic
        action – such as a pan or rotation.
    </p>
    <p>
        Gesture recognizers offer a much higher level of interpretation of mouse-like
        events, and they’re associated with views and can intercept all the mouse-like
        events associated with that view.
    </p>
    <p>
        The event handling architecture in OS X is quite complicated, but the
        defaults go a long way to handling many common cases. The power of the
        responder chain makes it easy to handle events at the highest level possible.
    </p>
    <h3>
        Menus
    </h3>
    <p>
        Menus are collections of different actions that you can associate with
        your app. Menus can appear in different places, including:
    </p>
    <ul>
        <li>
            <em>
                Menu Bar
            </em>
            this is bar along the top of the screen
            <br>
            <img class="aligncenter size-medium wp-image-111910" src="https://koenig-media.raywenderlich.com/uploads/2015/08/menu_bar-480x283.png"
            alt="menu_bar" width="480" height="283" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/menu_bar-480x283.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/08/menu_bar-700x412.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/08/menu_bar.png 842w"
            sizes="(max-width: 480px) 100vw, 480px">
        </li>
        <li>
            <em>
                Context Menus
            </em>
            appear when the user right clicks
            <br>
            <img class="aligncenter size-medium wp-image-111904" src="https://koenig-media.raywenderlich.com/uploads/2015/08/context_menu-480x291.png"
            alt="context_menu" width="480" height="291" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/context_menu-480x291.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/08/context_menu.png 578w"
            sizes="(max-width: 480px) 100vw, 480px">
        </li>
        <li>
            <em>
                Dock Menu
            </em>
            when the user long-presses the dock icon
            <br>
            <img class="aligncenter size-medium wp-image-111905" src="https://koenig-media.raywenderlich.com/uploads/2015/08/dock_menu-270x320.png"
            alt="dock_menu" width="270" height="320" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/dock_menu-270x320.png 270w, https://koenig-media.raywenderlich.com/uploads/2015/08/dock_menu-422x500.png 422w, https://koenig-media.raywenderlich.com/uploads/2015/08/dock_menu.png 466w"
            sizes="(max-width: 270px) 100vw, 270px">
        </li>
    </ul>
    <p>
        All of these menus can be configured in Interface Builder, allowing you
        to configure their appearance, the hierarchy they appear in and to associate
        actions with each item.
    </p>
    <p>
        <img class="aligncenter size-medium wp-image-111906" src="https://koenig-media.raywenderlich.com/uploads/2015/08/ib_menu-480x127.png"
        alt="ib_menu" width="480" height="127" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/ib_menu-480x127.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/08/ib_menu-700x185.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/08/ib_menu.png 884w"
        sizes="(max-width: 480px) 100vw, 480px">
    </p>
    <h2>
        Data Layer
    </h2>
    <p>
        The user interface is an enormously important part of your OS X app, but
        it’s probably not the
        <i>
            entirety
        </i>
        of your app. Most apps provide a user interface so that users can interact
        with an underlying data model.
    </p>
    <p>
        Data models depend heavily on the domain in which your app exists – there’s
        no magical solution to building a data layer. In fact, it’s often the case
        that you’ll use the object oriented language features available in Swift
        to create a set of objects that model the domain of your app.
    </p>
    <p>
        It’s extremely important that the data layer should be separated out from
        the user interface, making your software your software more maintainable
        and less error-prone. OS X supports this architecture through Cocoa Bindings
        – a technology that wires up model objects to the UI and ensures that they
        are automatically kept in sync with each other.
    </p>
    <p>
        You can create a completely separate dynamic framework to contain your
        data layer – completely separating it from the UI layer. This can allow
        the same data layer to be used in multiple apps – possibly even shared
        between an OS X and an iOS app, and increases testability.
    </p>
    <p>
        Although you can create your own data layer, Apple provides a framework
        called Core Data. This is a comprehensive framework for creating an object
        graph to completely model your entire data layer. It supports persistence
        to disk, data validation, undo and much more.
    </p>
    <p>
        Core Data has great support for Cocoa Bindings, meaning that it’s really
        easy to integrate your model editing UI with a Core Data backend to build
        the bulk of your app really quickly.
    </p>
    <h2>
        Other useful Cocoa functionality
    </h2>
    <p>
        This article has given you a very brief overview of some of the Cocoa
        concepts that are likely to be used in every single OS X app. This barely
        scrapes the surface of what is a very rich platform.
    </p>
    <p>
        Some highlights of other parts of Cocoa that are extremely useful when
        building powerful OS X apps:
    </p>
    <ul>
        <li>
            <em>
                Networking
            </em>
            : In addition to access to the very lowest level of networking functionality,
            OS X provides a much higher-level API for handling HTTP requests. The networking
            model is built around an asynchronous session – seamlessly handling uploads
            and downloads as a list of tasks.
        </li>
        <li>
            <em>
                Location
            </em>
            : You might associate location-based services primarily with mobile devices,
            but you have full access to a lot of powerful functionality both about
            location through Core Location, and for mapping using MapKit.
        </li>
        <li>
            <em>
                WebKit
            </em>
            : Safari is one of the top web browsers, and you can integrate the powerful
            rendering engine into your own app via WebKit. It also includes the ability
            to interact with the content, and to render HTML content from a selection
            of sources.
        </li>
    </ul>
    <h2>
        Where to go from here?
    </h2>
    <div class="inline-video-ad" id="sub-banner-inline">
        <div class="inline-video-ad-wrapper">
            <a href="https://videos.raywenderlich.com/courses" sl-processed="1">
                <div class="col-wrapper">
                    <div class="col">
                        <img src="https://cdn3.raywenderlich.com/wp-content/themes/raywenderlich/images/global/video-yeti@2x.png"
                        alt="yeti holding videos">
                    </div>
                    <div class="col large-col">
                        <span>
                            Want to learn even faster? Save time with our
                            <span>
                                video courses
                            </span>
                        </span>
                    </div>
                </div>
            </a>
        </div>
    </div>
    <p>
        This article has given you an overview of how Cocoa apps for OS X fit
        together, but it hasn’t given you a great idea of how you can actually
        use this to get started creating apps. Fear not – for that is the purpose
        of the
        <a href="http://www.raywenderlich.com/110269/mac-os-x-development-tutorial-for-beginners-part-3-your-first-os-x-app"
        sl-processed="1">
            next article
        </a>
        in this introductory series.
    </p>
    <p>
        If you’d like to learn more about the theoretical side of building OS
        X apps then Apple has provided a good guide to Cocoa apps as part of the
        documentation guides. It’s not especially helpful at the practical aspects
        of building apps, but if you read it in its entirety then you’ll know an
        awful lot about Cocoa!
    </p>
    <p>
        As ever, if you have any questions or comments feel free to get involved
        on the forums or leave a comment below.
    </p>
</div>