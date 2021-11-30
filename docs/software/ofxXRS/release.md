# Release Guide
So, you've developed your app to the point where it's ready for end users.
There are a few things we have to do to prepare the app for release.

# Removing the Debug Console
First, you'll want to get rid of the debug console that pops up when you run the application (keep in mind once this is disabled you will not be able to view any `std::cout` unless you run the app in Visual Studio).

You first need to change Visual Studio's Linker settings to instruct it to compile a windows application rather than a console application:
1. Right click on your app's project in the Solution Explorer and select **Properties**
2. In the properties menu that appears, navigate to Linker > System > Subsystem
3. Set the Subsytem from `Console (/SUBSYSTEM:CONSOLE)` to `Windows (/SUBSYTEM:WINDOWS)`

<p>&nbsp;</p>

Now let's alter our executable to properly use this subsystem:
1. Open your main.cpp in Visual Studio
2. Change the `int main()` entry point to:  
 `int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine, int nShowCmd)`

That's all! Now your app should start without the console.

<p>&nbsp;</p>

# Adding an Icon

# Building and Releasing