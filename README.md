# DeveTPLDataflowVisualizer

This is a library to easily visualize the progress of a TPL Dataflow in a Console application.

<img src="visualizer.gif" width="500">

Usage instructions:
To use this library you should replace all existing TPL Dataflow block names with Deve*****Block. E.g. change:

```csharp
var blockOld = new TransformManyBlock<int, string>((input) =>
{
    return Enumerable.Range(0, input).Select(t => $"Super test: {t}");
});
```
To:

```csharp
var blockNew = new DeveTransformManyBlock<int, string>("Video -> Frame", (input) =>
{
    return Enumerable.Range(0, input).Select(t => $"Super test: {t}");
});
```

After that you can use the following piece of code to visualize the different blocks:

```csharp
_ = Task.Run(async () =>
{
    var baume = new Tree("Root");
    var baumeNode = new TreeNode(new Text("RootNode"));
    baume.AddNode(baumeNode);
    AnsiConsole.Live(baume)
        .Start(ctx =>
        {
            while (true)
            {
                baumeNode.Nodes.Clear();
                SpectreConsoleRenderer.SuperBaumenMacher(b1_extractFramesFromVideo, baumeNode, (block) => block == b1_extractFramesFromVideo ? 1 : b1_broadcast.ProcessedCount);
                ctx.Refresh();
                Thread.Sleep(50);
            }
        });
});
```

For more information see the example [Program.cs](DeveTPLDataflowVisualizer.ConsoleApp/Program.cs)

Also, I'm not even german, I was just in a funny mood when making up the names for the `SuperBaumenMacher`...

## Internal workings

All Deve....Blocks extend the DeveBaseBlock which wraps the internal Actions and counts up all executions of Actions that are being processed / have been processed.

## Build status

| GitHubActions Builds |
|:--------------------:|
| [![GitHubActions Builds](https://github.com/devedse/DeveTPLDataflowVisualizer/workflows/GitHubActionsBuilds/badge.svg)](https://github.com/devedse/DeveTPLDataflowVisualizer/actions/workflows/githubactionsbuilds.yml) |

## Intellicode

|  Github Actions (Intellicode) |
|:-----------------------------:|
| [![GitHubActions Builds](https://github.com/devedse/DeveTPLDataflowVisualizer/workflows/GitHubActionsBuilds/badge.svg)](https://github.com/devedse/DeveTPLDataflowVisualizer/actions?query=GitHubActionsBuilds) |

## DockerHub

| Docker Hub |
|:----------:|
| [![Docker pulls](https://img.shields.io/docker/v/devedse/devetpldataflowvisualizerconsoleapp)](https://hub.docker.com/r/devedse/devetpldataflowvisualizerconsoleapp/) |

## Code Coverage Status

| CodeCov |
|:-------:|
| [![codecov](https://codecov.io/gh/devedse/DeveTPLDataflowVisualizer/branch/master/graph/badge.svg)](https://codecov.io/gh/devedse/DeveTPLDataflowVisualizer) |

## Code Quality Status

| SonarQube |
|:---------:|
| [![Quality Gate](https://sonarcloud.io/api/project_badges/measure?project=DeveTPLDataflowVisualizer&metric=alert_status)](https://sonarcloud.io/dashboard?id=DeveTPLDataflowVisualizer) |

## Package

| NuGet |
|:-----:|
| [![NuGet](https://img.shields.io/nuget/v/DeveTPLDataflowVisualizer.svg)](https://www.nuget.org/packages/DeveTPLDataflowVisualizer/) |