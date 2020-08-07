## Description
This is my Images to C# Console converter. Right now, It only support PNG files.
## How to use it
It's pretty simple, you only have to depose the PNG files into "Images" and execute the application.

Once the Console close, check in the "Output" folder and there will be two or mores (depending at how many pictures you
inserted into the folder) text files containing the Console.WriteLine commands. Just copy paste anywhere you want.

For the transparent pixels (like a green screen in videos), you'll need to put a background with the following RGB 
into your images.  (R : 179 G : 186 B: 216)

You picture also need to be small, like pixel art small. (The Rattata I use for my example is 18 x 21 pixels)

##Example

![enter image description here](https://i.imgur.com/MmykaSG.png)

Result

![enter image description here](https://i.imgur.com/hgZGIce.png)

##Requirement
Windows 10 Anniversay Update:

You need to have the 256 colors enable, to do so, you simply need to add this to your program.cs


class Program

{

	[DllImport( "kernel32.dll", SetLastError = true )]
	
	public static extern bool SetConsoleMode( IntPtr hConsoleHandle, int mode );
	[DllImport( "kernel32.dll", SetLastError = true )]
	
	public static extern bool GetConsoleMode( IntPtr handle, out int mode );
	[DllImport( "kernel32.dll", SetLastError = true )]
	
	public static extern IntPtr GetStdHandle( int handle );

	static void Main( string[] args )
	{
		var handle = GetStdHandle( -11 );
		int mode;
		GetConsoleMode( handle, out mode );
		SetConsoleMode( handle, mode | 0x4 );

	}
}

Documentation for the 256 colours : https://github.com/tomakita/Colorful.Console/issues/24
