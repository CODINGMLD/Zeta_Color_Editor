## Zeta Color Editor

<h2>Introduction</h2>

> For the latest version of our Desktop CMS "Zeta Producer Desktop 8", I was in need to allow the user selecting colors.

> The reason why I decided to develop my own color picker was that after having used some other color picker controls in the past, none of them finally matched 100% of my needs. So I ended up developing my very own version (nearly) from scratch.

> Therefore my color picker probably does not fit 100% for your requirements. But at least if I can give you a basis that you can build on and extend, I am already very happy!


<h2>Features</h2>

> The color picker comes either as a stand-alone form to show, or it comes as a control to embed into your own forms. The example included also contains property grid editor to allow for in-place editing of colors in a standard PropertyGrid control.

> Basically, I wanted to have a great looking control and also a reasonably understandable code behind (i.e. no quickly hacked together features). I really hope I have achieved these goals.

> The Zeta Color Editor library comes with English and German translations. It is easy to add your own, especially if you use a tool like this one.

> The following features are included

<h2>Custom Colors</h2>

> The first tab in the form/control.

![0](https://user-images.githubusercontent.com/65526236/224452518-0a8fd5e0-666b-40c2-815d-12d6b326c196.PNG)

> Allows your users to select a color from a color palette by dragging the two cursors (cross and arrow), directly entering in RGB or HSL color space or entering the HTML color code.

<h2>Web Colors</h2>

> This is the second tab in the form/control.

![2](https://user-images.githubusercontent.com/65526236/224452596-a5913aaa-27c9-490e-ab93-217ed95f0728.PNG)

> Shows named colors and lets the user select one of them.

<h2>Browser-safe Colors</h2>

> This is the third tab in the form/control.

![4](https://user-images.githubusercontent.com/65526236/224452753-97a5bdab-1e8a-45a3-9a67-d7ec65390eb0.PNG)

> Allows the user to select browser-safe colors.

<h2>System Colors</h2>

> The fourth tab in the form/control.

![5](https://user-images.githubusercontent.com/65526236/224452778-0b264f01-0949-4e9f-810f-e06ee499ff50.PNG)

> Shows all system-known named colors for the different UI elements of Windows.

<h2>Schemes</h2>

> This is the fifth and last tab in the form/control.

![6](https://user-images.githubusercontent.com/65526236/224452834-81a5f27c-9d35-4382-8630-eaae358a6407.PNG)

> With the concept of schemes, you as the developer are able to provide an arbitrary number of additional lists of colors (the so called "schemes") to the Zeta Color Editor library.

> Inside our Zeta Producer application, we have a number of different layouts, each of which has its own custom palette. With the help of schemes, we enable the users to select from the different palettes of the different layouts.

> So the scheme concept allows you to flexibly extend the color picker.

<h2>Using the Code</h2>

> The download above contains the library as well as a small example project:

![1](https://user-images.githubusercontent.com/65526236/224452915-cb700dad-1add-4924-a778-36a01d4568ca.PNG)

> The example project shows you how to easily integrate the library into your own projects.

> For example, the following code is the complete content of the Click handler of the example project:

```
C#
```
```
private void launchColorEditorButton_Click( object sender, EventArgs e )
{
    using ( var form = new ColorEditorForm() )
    {
        // Must set the extender _first_, since it helps in lookup
        // of the selected color.
        form.ExternalColorEditorInformationProvider = new ExternalTestProvider();
        form.SelectedColor = colorPanel.BackColor;

        if ( form.ShowDialog( this ) == DialogResult.OK )
        {
            colorPanel.BackColor = form.SelectedColor;
        }
    }
}
```

> Simply create an instance of the ColorEditorForm, passing initial properties and an (optional) provider for the color schemes and call the ShowDialog method.

> If the form was closed with the "OK" or the "No color" button, the ShowDialog method returns DialogResult.OK. Read the SelectedColor property of the form to retrieve the color.
