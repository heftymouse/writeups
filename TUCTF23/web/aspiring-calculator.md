# Aspiring Calculator

This is based around a Razor template injection in an ASP.NET Core server. The calculator is essentially a form that compiles and evaluates your expression using RazorEngine. The UI only allows a handful of operations with just numbers, but the form simply sends your expression as a string. The evaluated output of the expression is sent in the response as the value of the result text box.

As such, we can execute arbitrary code on the server by making a request to the form with any C# expression of our choice.

The flag is not present on the filesystem or environment variables. It is part of the server binary itself - which we can easily obtain using our RCE.

```cs
System.Convert.ToBase64String(System.IO.File.ReadAllBytes("/app/challenge.dll"))
```

This will send challenge.dll as a Base64-encoded blob in the result box, which can be decoded locally using your tool of choice. We can now simply use `strings` on the obtained challenge.dll to obtain the flag.