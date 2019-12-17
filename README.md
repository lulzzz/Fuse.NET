<p align="center">
![logo.png]
</p>

## Introduction

A lightweight zero-dependency C# port of the Fuse.js fuzzy-search library created by [@krisk](https://github.com/krisk) at https://github.com/krisk/Fuse

## Licenses

You can find the original license in the `LICENSE.ORIGINAL` file, and the license for this derivative work in the `LICENSE.DERIVATIVE` file.

## Example Usage

```csharp
public struct Book
{
	public string title;
	public string author;
}

// This test data was taken from the fixtures in Fuse.js.
var input = new List<Book>();

input.Add(new Book
{
	title = "The code of the wooster",
	author = "aa"
});

input.Add(new Book
{
	title = "the wooster code",
	author = "aa"
});

input.Add(new Book
{
	title = "The code",
	author = "aa"
});

input.Add(new Book
{
	title = "Old Man's War",
	author = "John Scalzi"
});

input.Add(new Book
{
	title = "The Lock Artist",
	author = "Steve Hamilton"
});

var opt = new FuseOptions();

opt.includeMatches = true;
opt.includeScore = true;

// Here we search through a list of `Book` types but you could search through just a list of strings.
var fuse = new Fuse<Book>(input, opt);

fuse.AddKey("title");
fuse.AddKey("author");

var output = fuse.Search("wooster");

output.ForEach((a) =>
{
	Debug.Log(a.item.title + ": " + a.item.author);
	Debug.Log("Score: " + a.score);

	if (a.matches != null)
	{
		a.matches.ForEach((b) =>
		{
			Debug.Log("{Match}");
			Debug.Log(b.key + ": " + b.value + " / " + b.indicies.Count);
		});
	}
});
```

## Installation

Drag and drop the Fuse.NET folder directly into your C# project.
```

## Contributing

Contributions are welcome, if you have one to make please don't hestitate to create a pull request.