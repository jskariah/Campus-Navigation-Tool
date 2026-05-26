# OpenStreetMaps Pathfinding Project

## Overview

This project is a C++ OpenStreetMaps pathfinding application that builds a weighted directed graph from map data and uses Dijkstra's algorithm to find shortest paths between campus buildings.

The application parses OpenStreetMap-style JSON data, stores buildings and waypoints as graph vertices, connects paths with weighted edges based on geographic distance, and allows users to find walking routes between locations.

The main implementation work was completed in:

- `graph.h`
- `application.cpp`

## Features

- Custom templated graph implementation
- Directed weighted graph using an adjacency list
- OpenStreetMap-style JSON parsing
- Building and waypoint graph construction
- Distance calculation using latitude and longitude
- Shortest pathfinding with Dijkstra's algorithm
- Building lookup by abbreviation or partial name
- Text-based pathfinding interface
- Optional local web server for visualizing paths

## Technologies Used

- C++
- Templates
- STL containers
- Unordered maps
- Sets
- Priority queue
- JSON parsing
- Graph algorithms
- Dijkstra's algorithm
- Makefile
- Local HTTP server support

## Project Structure

```text
OpenStreetMaps/
├── graph.h
├── application.cpp
├── application.h
├── dist.cpp
├── dist.h
├── main.cpp
├── server.cpp
├── httplib.h
├── json.hpp
├── suppr.txt
├── .gitattributes
├── .gitignore
└── README.md
```

## File Descriptions

| File | Description |
|---|---|
| `graph.h` | Custom templated directed weighted graph implementation |
| `application.cpp` | Builds the map graph and implements pathfinding logic |
| `application.h` | Function declarations and building data structures |
| `dist.cpp` | Distance and coordinate helper functions |
| `dist.h` | Coordinate structure and distance function declarations |
| `main.cpp` | Runs the command-line map navigation program |
| `server.cpp` | Runs the local web server for visual pathfinding |
| `httplib.h` | Header-only HTTP server library |
| `json.hpp` | Header-only JSON library |
| `suppr.txt` | AddressSanitizer suppression file |
| `.gitattributes` | Git line-ending configuration |

## Graph Implementation

The project includes a custom `graph<VertexT, WeightT>` class implemented with an adjacency list.

The graph supports:

- Adding vertices
- Adding directed weighted edges
- Updating existing edge weights
- Getting edge weights
- Finding neighboring vertices
- Getting all vertices
- Counting vertices
- Counting edges

The graph is used to represent map data where:

- Vertices represent buildings and waypoints
- Edges represent walkable paths
- Edge weights represent geographic distance in miles

## Map Graph Construction

The `buildGraph` function reads JSON map data and constructs the graph.

It processes:

- Buildings
- Waypoints
- Footways

The function:

1. Adds buildings as graph vertices
2. Adds waypoints as graph vertices
3. Connects consecutive footway nodes with weighted edges
4. Connects nearby buildings to footway nodes
5. Stores building and coordinate information for later pathfinding

## Dijkstra's Algorithm

The project uses Dijkstra's algorithm to find the shortest path between two locations.

The algorithm:

1. Starts at the selected starting building
2. Tracks shortest known distances to each node
3. Uses a priority queue to process the closest unvisited node
4. Stores predecessors to reconstruct the final path
5. Returns the shortest path as a list of node IDs

The implementation also supports ignored nodes, which is useful for avoiding buildings as intermediate path nodes while still allowing the start and destination buildings.

## Building Search

Users can search for buildings using:

- Exact building abbreviation
- Partial building name

For example, a user may search for a building by typing its abbreviation or part of its full name.

The command-line version loads the map data, builds the graph, prints graph statistics, and then allows the user to search for paths between buildings.

## Example Program Flow

```text
** Navigating UIC open street map **
# of buildings: ...
# of vertices: ...
# of edges: ...

Enter start building:
Enter destination building:
```

The program then finds and prints the shortest path between the selected buildings.

## What I Learned

Through this project, I practiced:

- Implementing a graph from scratch
- Using adjacency lists to represent graph connections
- Working with templated C++ classes
- Parsing structured JSON map data
- Representing real-world map information as a graph
- Calculating distances between geographic coordinates
- Implementing Dijkstra's shortest path algorithm
- Using priority queues for efficient pathfinding
- Reconstructing paths using predecessor tracking
- Building a complete command-line application
- Connecting backend pathfinding logic to a local visualization server

## Notes

This repository is intended to showcase the implementation and functionality of the OpenStreetMaps pathfinding project.

Generated build files, compiled executables, editor-specific files, and course handouts are intentionally excluded from the repository.

## Future Improvements

Potential future improvements include:

- Adding support for multiple transportation modes
- Improving route visualization
- Adding estimated walking time
- Supporting alternate route suggestions
- Improving building search with fuzzy matching
- Adding path distance summaries
- Supporting larger map datasets
- Adding a graphical interface with route highlighting

## Author

Created by Justin Skariah.

Primary implementation work completed in `graph.h` and `application.cpp`.
