# GlobalMessage

A lightweight, customizable message system for Unity games and applications. GlobalMessage provides smooth fade animations and flexible configuration for displaying important information to your players.

## Features

- ✨ Smooth fade in/out animations powered by PrimeTween
- 🔄 Auto-close functionality with configurable duration
- 🖱️ Optional close button for user interaction
- ⏱️ Time-scale independent animations (works during paused gameplay)
- 🎯 Simple API for showing messages from anywhere in your code

## Installation

### Requirements

- Unity 2022.1 or newer
- TextMesh Pro (com.unity.textmeshpro)
- PrimeTween (com.kybernetik.primetween or appropriate package name)

### Package Dependencies

Add the following to your `manifest.json` or package dependencies:

```json
"dependencies": {
  "com.unity.textmeshpro": "3.0.6",
  "com.kybernetik.primetween": "1.2.2
}
```

## Setup

1. Import the GlobalMessage package
2. Add the `GlobalMessageComponent` prefab to your persistent UI Canvas
3. Ensure the prefab has the following components set up:
   - CanvasGroup (required)
   - TMP_Text for displaying messages
   - Button (optional) for manual closing

## Usage

### Basic Usage

```csharp
// Reference to your GlobalMessageComponent
[SerializeField] private GlobalMessage.Runtime.GlobalMessageComponent messageComponent;

// Show a message
messageComponent.ShowMessage("Item collected!");
```

### Access From Anywhere

For easy access throughout your project, consider creating a static accessor:

```csharp
public static class GlobalMessageManager
{
    private static GlobalMessageComponent _instance;
    
    public static void Initialize(GlobalMessageComponent component)
    {
        _instance = component;
    }
    
    public static void ShowMessage(string message)
    {
        if (_instance != null)
            _instance.ShowMessage(message);
    }
}

// Then use it from anywhere
GlobalMessageManager.ShowMessage("Level Complete!");
```

## Configuration

All settings can be adjusted in the Inspector:

| Property | Description | Default |
|----------|-------------|---------|
| FadingDuration | Duration of fade in/out animations in seconds | 0.5 |
| ShouldAutoClose | Whether messages close automatically | true |
| ShowingDuration | How long messages stay visible before auto-closing | 2.0 |
| Button | Optional button reference for manual closing | null |

## Customization

You can extend the functionality by:

- Styling the TMP_Text component
- Adding additional animations
- Implementing queuing for multiple messages
- Adding sound effects

## License

[Your license information here]