# MFTPubSubData
SQLite database with simulation output data for the MFTPubSub and AODV protocols using [Castalia](https://github.com/boulis/Castalia) and [OMNeT++](https://omnetpp.org/).

The database contains two tables one for storing information about a unique simulation and another that stores the results for each node in the simulation:

Table `simulation`:

| Column       | Description                                                                                                       |
| ------------ | ----------------------------------------------------------------------------------------------------------------- |
| ID           | Simulation identifier                                                                                             |
| algorithm    | The routing protocol used in the simulation. MFTPubSub or AODV                                                    |
| fieldx       | Width of the simulation area                                                                                      |
| fieldy       | Height of the simulation area                                                                                     |
| nodes        | Number of nodes in the simulation                                                                                 |
| mobilityType | Mobility pattern used for the simulation. Random Waypoint in this case for all simulations                        |
| speed        | The maximum speed for the nodes in the simulation                                                                 |
| seedOffset   | An offset applied to the random seed for the mobility pattern, allowing for different scenarios in the simulation |

Table `results`:

| Column       | Description                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------- |
| simulationID | References the `simulation` identifier                                                                                        |
| nodeID       | Identifier of the node in each simulation                                                                                     |
| toReceive    | Number of publication messages the node should have received, calculated since the network knows of the existence of the node |
| received     | Number of publication messages received                                                                                       |
| PUB          | Number PUB messages received                                                                                                  |
| REP          | Number of REP messages received                                                                                               |
| migrations   | Number of times the given node has migrated                                                                                   |
| mhops        | Average number of hops a publication message needed in order to arrive to this node                                           |
| mtime        | Average time a publication message needed in order to arrive to this node                                                     |
| MACSent      | Total number of messages sent by this node                                                                                    |
