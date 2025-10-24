# Tools & Setup - Development Environment

Setting up your development environment for MineWorld-SDK development.

## 🛠️ Required Tools

### 1. .NET 9 SDK
**Purpose**: C# runtime and development tools

**Download**: https://dotnet.microsoft.com/download/dotnet/9.0

**Verify Installation**:
```bash
dotnet --version
# Should show: 9.0.x
```

### 2. IDE (Choose One)

#### Visual Studio 2022 (Recommended)
**Download**: https://visualstudio.microsoft.com/vs/
**Required Workloads**:
- .NET desktop development
- Game development with C++ (for graphics debugging)

**Pros**: Best C# support, integrated debugging, IntelliSense
**Cons**: Windows only, large download

#### JetBrains Rider
**Download**: https://www.jetbrains.com/rider/
**Required Plugins**: None (C# support built-in)

**Pros**: Cross-platform, excellent C# support, lightweight
**Cons**: Paid (free trial available)

#### Visual Studio Code
**Download**: https://code.visualstudio.com/
**Required Extensions**:
- C# Dev Kit
- C# Extensions
- GitLens

**Pros**: Free, lightweight, cross-platform
**Cons**: Less integrated than full IDEs

### 3. Git
**Purpose**: Version control

**Download**: https://git-scm.com/

**Verify Installation**:
```bash
git --version
# Should show: git version 2.x.x
```

### 4. MineWorld Game
**Purpose**: Game dependency for testing mods

**Installation**: Will be used for testing mod installations

## 🎮 Modding-Specific Tools

### 1. Content Creation Tools

#### Blender (3D Modeling)
**Purpose**: Create 3D models and textures
**Download**: https://www.blender.org/

**MineWorld Use Cases**:
- Creating custom block models
- Texture creation and editing
- Asset optimization

#### GIMP (Image Editing)
**Purpose**: Texture editing and creation
**Download**: https://www.gimp.org/

**Alternative**: Adobe Photoshop, Paint.NET

#### Audacity (Audio Editing)
**Purpose**: Sound effect creation
**Download**: https://www.audacityteam.org/

**MineWorld Use Cases**:
- Creating custom sound effects
- Music composition
- Audio optimization

### 2. CLI Development Tools

#### System.CommandLine
**Purpose**: CLI framework for SDK tools
```bash
dotnet add package System.CommandLine
```

#### Handlebars.Net
**Purpose**: Template processing
```bash
dotnet add package Handlebars.Net
```

#### System.Text.Json
**Purpose**: JSON processing
```bash
dotnet add package System.Text.Json
```

## 🔧 Development Environment Setup

### 1. Project Structure
```
MineWorld-SDK/
├─ src/
│   ├─ MineWorld-SDK.CLI/
│   ├─ MineWorld-SDK.Templates/
│   ├─ MineWorld-SDK.Validation/
│   ├─ MineWorld-SDK.Packaging/
│   └─ MineWorld-SDK.Installation/
├─ tests/
├─ templates/
├─ docs/
└─ MineWorld-SDK.sln
```

### 2. CLI Project Setup
```csharp
// Program.cs
using System.CommandLine;

var rootCommand = new RootCommand("MineWorld SDK CLI Tool");

var newCommand = new Command("new", "Create new mod");
var typeArgument = new Argument<string>("type", "Mod type");
var nameArgument = new Argument<string>("name", "Mod name");

newCommand.AddArgument(typeArgument);
newCommand.AddArgument(nameArgument);
newCommand.SetHandler((type, name) => {
    Console.WriteLine($"Creating {type} mod: {name}");
}, typeArgument, nameArgument);

rootCommand.AddCommand(newCommand);
return await rootCommand.InvokeAsync(args);
```

## 🌐 Cross-Platform Considerations

### Windows Development
- **Shell**: PowerShell, cmd.exe
- **Path Separator**: `\`
- **Package Manager**: Chocolatey
- **CLI Tools**: Windows Terminal

### Linux Development
- **Shell**: Bash, Zsh
- **Path Separator**: `/`
- **Package Manager**: apt, yum, pacman
- **CLI Tools**: Terminal emulator

### macOS Development
- **Shell**: Zsh, Bash
- **Path Separator**: `/`
- **Package Manager**: Homebrew
- **CLI Tools**: Terminal.app

## 🚀 Verification Steps

### 1. Test .NET Installation
```bash
dotnet new console -n TestApp
cd TestApp
dotnet run
# Should print: Hello, World!
```

### 2. Test CLI Framework
```csharp
// Create simple CLI app
dotnet new console -n TestCLI
cd TestCLI
dotnet add package System.CommandLine
```

### 3. Test Content Creation Tools
- Open Blender and create a simple cube
- Open GIMP and create a simple texture
- Open Audacity and record a simple sound

## 🎯 Next Steps

1. **Install Required Tools**: .NET 9 SDK, IDE, Git
2. **Install Content Tools**: Blender, GIMP, Audacity
3. **Set up CLI Project**: Create basic CLI structure
4. **Test Environment**: Verify everything works
5. **Start Learning**: [v0.1 Learning Guide](v0.1/what-you-will-learn.md)

## 🆘 Troubleshooting

### Common Issues

**"dotnet command not found"**:
- Add .NET SDK to PATH
- Restart terminal/IDE

**"MineWorld not found"**:
- Verify MineWorld game installation
- Check game path configuration

**"Content tools not working"**:
- Update graphics drivers
- Check file permissions
- Verify tool installations

---

**Ready to start coding? Head to [v0.1 Learning Guide](v0.1/what-you-will-learn.md)!**
