# Pursuit-Core-iOS-Programmatic-UI-Lab

## Color Guessing Game: This time it's programmatic

In Unit 2, you built a [color guessing game](https://github.com/joinpursuit/Pursuit-Core-iOS-ColorGuessingGameExercise/blob/master/README.md) using Storyboard and Interface Builder.

For this lab, the requirements are the same, but you cannot use a Storyboard file or Interface builder to put your app together.

You can reuse your model from the other project: focus here on putting the view together programmatically.

You can also use the model provided below:

<details>
  <summary>ColorGuessingModel</summary>

```swift
import Foundation
import UIKit

class ColorGuessingModel {
    
    private var currentColor: UIColor
    private var currentDominantRGBColor: UIColor
        
    func getNewColor() -> UIColor {
        let randomColorTuple = ColorGuessingModel.randColor()
        currentColor = randomColorTuple.color
        currentDominantRGBColor = randomColorTuple.dominantColor
        
        return currentColor
    }
    
    func isDominant(guess: UIColor) -> Bool {
        return currentDominantRGBColor == guess
    }
        
    static private func randColor() -> (color: UIColor, dominantColor: UIColor) {
        let redValue = CGFloat(drand48())
        let greenValue = CGFloat(drand48())
        let blueValue = CGFloat(drand48())
        let color = UIColor(displayP3Red: redValue, green: greenValue, blue: blueValue, alpha: 1)
        let dominantColor: UIColor
        if max(redValue, greenValue, blueValue) == redValue {
            dominantColor = UIColor.red
        } else if max(redValue, greenValue, blueValue) == greenValue {
            dominantColor = UIColor.green
        } else {
            dominantColor = UIColor.blue
        }
        return (color, dominantColor)
        
    }
    
    init() {
        let randomColorTuple = ColorGuessingModel.randColor()
        let currentColor = randomColorTuple.color
        let currentDominantColor = randomColorTuple.dominantColor
        
        self.currentColor = currentColor
        self.currentDominantRGBColor = currentDominantColor
    }
}
```
</details>

## Overview (Copied from the project link above)

The name of the game is generating and guessing random colors.

Have the app generate and display a random color from RGB values.

The user is to guess which RGB value is most dominant (ie, the largest), by pressing one of three buttons, red, green or blue.

When the user selects the correct color, the game increments the current score and selects a new random color.

When the user selects the incorrect color, the game ends and the user should have the option to play again.

The game should keep track of the highest score (while the app is running).

Your app should have a model and implement MVC where possible.



### Stage 1: 

Create three buttons for red, green and blue. Create a UIView that displays just red, green or blue randomly. 

If the user clicks the button for the displayed color, the app should display a new color and the user able to guess again.
If the user clicks the wrong button the game should end and the user should have the option to play again.

### Stage 2: 

Have the app keep score of the correct guesses.

### Stage 3: 

Have the game generate a random color using the below UIColor initializer...

```swift
let myColor = UIColor(red: CGFloat, green: CGFloat, blue: CGFloat, alpha: CGFloat)
```

You can generate random CGFloats between 0 and 1 using...

```swift
let randNum = CGFloat.random(in: 0...1)
```

### Stage 4:

Have the app keep track of the highest score (so long as it is running)


### Bonus:


Try to refactor any duplicated code into functions.

The game is kinda easy. Change your code so that the random colors generated have rgb values that are closer together.

Add the ability for the user to select the dificulty level. 
