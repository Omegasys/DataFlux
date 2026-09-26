# DataFlux

DataFlux is a modular, high-performance file transfer and data management platform designed to provide fast, reliable, secure, and highly configurable data movement across local storage, networks, remote systems, and removable devices.

DataFlux combines the capabilities commonly found in advanced file-copy utilities, synchronization tools, backup applications, and network transfer clients into a single transfer engine.

The goal is simple:

> Move data efficiently, safely, securely, and according to the user's rules.

## Features

### High-Performance Transfers

DataFlux can intelligently transfer multiple files at the same time while adapting its behavior to the hardware and workload.

Features include:

* Parallel file transfers
* Adaptive worker counts
* Sequential transfer mode
* SSD/NVMe optimization
* HDD-aware scheduling
* Network-aware parallelism
* Adaptive buffering
* Transfer prioritization
* Queue management
* Transfer dependencies
* Live transfer statistics
* Automatic performance optimization

DataFlux does not blindly maximize parallelism. It can analyze the source, destination, storage devices, and workload and select an appropriate transfer strategy.

## Copy and Move Operations

DataFlux supports common filesystem operations including:

* Copy
* Move
* Delete
* Rename
* Recursive transfers
* Batch operations
* Dry runs
* Rollback support
* Operation previews

Operations can be planned before execution so that users can review what DataFlux intends to do.

## Multiple Transfer Jobs

Multiple transfer jobs can run simultaneously.

Each job can have its own:

* Priority
* Worker count
* Bandwidth limit
* Security configuration
* Verification method
* Conflict policy
* Source
* Destination
* Transfer profile

Jobs can be paused, resumed, cancelled, reordered, and monitored independently.

## Intelligent Parallelism

DataFlux can automatically determine how much parallelism is appropriate for a transfer.

Possible strategies include:

* Automatic
* Sequential
* Balanced
* Maximum throughput
* Minimum system impact
* Maximum parallelism

The scheduler can consider:

* HDD vs SSD vs NVMe
* Source and destination devices
* Whether source and destination share a physical device
* Network bandwidth
* CPU utilization
* Memory availability
* File sizes
* Number of files
* Current system workload

This allows DataFlux to avoid situations where excessive parallelism actually makes a transfer slower.

## Bandwidth and Rate Limiting

DataFlux provides granular transfer-rate controls.

Limits can be applied to:

* Entire application
* Individual transfer jobs
* Individual files
* File extensions
* File categories
* Folders
* Storage devices
* Destinations
* Network interfaces
* Time periods

For example:

```text
Global:
200 MB/s

Ethernet:
150 MB/s

*.iso:
50 MB/s

/home/user/linux.iso:
10 MB/s
```

More specific rules can override broader rules according to the configured rule priority.

Rate limits can also be changed while transfers are running.

## Network Transfers

DataFlux can transfer data across a variety of network connections and protocols.

Supported or planned connection types include:

* Ethernet
* Wi-Fi
* Internet
* VPN connections
* Cellular
* Bluetooth
* Local networks
* NAS devices
* Remote servers

Supported or planned protocols include:

* SMB
* SMB3
* NFS
* SFTP
* SSH
* FTP
* FTPS
* WebDAV
* HTTP
* HTTPS
* DataFlux Protocol

DataFlux can monitor network conditions and adjust transfer behavior accordingly.

## DataFlux-to-DataFlux Transfers

Two DataFlux installations can communicate directly with each other using the DataFlux Protocol.

This allows one DataFlux installation to act as a source while another acts as the destination.

DataFlux-to-DataFlux transfers can provide:

* Secure sessions
* Peer authentication
* Encrypted transfers
* Resumable transfers
* Chunk-based transfers
* Integrity verification
* Transfer manifests
* Parallel transmission
* Bandwidth control
* Connection recovery

## Secure Transfers

Security is a built-in part of DataFlux rather than a separate application.

Users can select the security level for each transfer.

Available security modes include:

* Normal
* Secure
* Maximum Security
* Encrypted Archive

### Security Options

Advanced transfer settings can include:

* Transport encryption
* End-to-end encryption
* Mutual authentication
* Peer identity verification
* Encrypted chunks
* Replay protection
* Integrity verification
* Secure session establishment
* Resumable encrypted transfers
* Encrypted destination storage

DataFlux is designed to use established, well-tested cryptographic protocols and libraries rather than inventing custom cryptography.

Cryptographic algorithms and implementations may be selected automatically according to the security policy and compatibility requirements.

## Transfer Security Selection

The graphical interface provides a security selection system for each transfer.

Example:

```text
Security Mode:
[ Maximum Security ]

Encryption:
[ Automatic ]

Peer Authentication:
[ Mutual ]

End-to-End Encryption:
[ Enabled ]

Encrypted Chunks:
[ Enabled ]

Replay Protection:
[ Enabled ]

Verification:
[ BLAKE3 ]
```

The same functionality can be configured through the command-line interface.

## Resumable Transfers

DataFlux is designed to recover from interrupted transfers.

Transfers can maintain checkpoints that allow them to resume after:

* Network interruptions
* Device disconnects
* Computer shutdowns
* Application crashes
* Temporary filesystem errors
* Remote connection failures

Large files can be transferred in chunks so that an interrupted transfer does not necessarily need to start again from the beginning.

## Verification

DataFlux can verify transferred data using multiple verification mechanisms.

Supported or planned methods include:

* Byte-for-byte comparison
* CRC32
* MD5
* SHA-1
* SHA-256
* SHA-512
* BLAKE2
* BLAKE3

Verification can be performed after a transfer or integrated into the transfer process.

BLAKE3 and other modern cryptographic hashes can be used where appropriate for fast integrity verification.

## Conflict Resolution

When the destination already contains a file with the same name, DataFlux provides configurable conflict handling.

Possible actions include:

* Replace
* Skip
* Rename
* Keep newest
* Keep oldest
* Compare sizes
* Compare timestamps
* Compare hashes
* Ask the user

Conflict policies can be stored in transfer profiles.

## Synchronization

DataFlux can also be used as a synchronization platform.

Synchronization modes include:

* One-way synchronization
* Two-way synchronization
* Mirror synchronization
* Incremental synchronization

Before applying synchronization changes, DataFlux can generate a preview showing what will be changed.

## Backup

DataFlux includes backup functionality designed around the same transfer engine.

Backup types include:

* Full backups
* Incremental backups
* Differential backups
* Versioned backups

Backup features include:

* Retention policies
* Backup verification
* Restore operations
* Backup profiles
* Version management

## Filtering

Transfers can be controlled using filters.

Filters can be based on:

* File extensions
* MIME types
* Folders
* File sizes
* Modification dates
* Regular expressions
* Hidden files

Both inclusion and exclusion rules are supported.

Example:

```text
Include:
*.iso
*.img
*.qcow2

Exclude:
*.tmp
*.cache
```

## Automation

DataFlux can automate recurring transfer operations.

Automation features include:

* Scheduled jobs
* Watched folders
* Drive events
* Network events
* Job triggers
* Pre-transfer commands
* Post-transfer commands

For example, DataFlux could automatically transfer files to a backup destination whenever a watched directory changes.

## Storage Awareness

DataFlux can inspect storage devices and use their characteristics when planning transfers.

Potential information includes:

* Device type
* Filesystem
* Available space
* Storage capacity
* Temperature
* SMART information
* Partition information
* Volume information
* Filesystem capabilities

This information can be used by the transfer optimizer when selecting a strategy.

## Duplicate Detection

DataFlux can identify duplicate files using metadata and hashes.

Duplicate detection can be used to:

* Find identical files
* Reduce redundant data
* Analyze storage usage
* Assist synchronization
* Assist backup planning

## Transfer Planning

Before executing a large operation, DataFlux can generate a transfer plan.

The plan can include:

* Source files
* Destination paths
* Estimated size
* Available destination space
* Conflicts
* Filters
* Transfer strategy
* Parallelism
* Bandwidth limits
* Security configuration
* Verification settings

Users can review the plan before execution.

## Command-Line Interface

DataFlux is designed to provide full command-line functionality in addition to its graphical interface.

Example:

```text
dataflux copy /source /destination
```

Example with additional options:

```text
dataflux copy /source /destination \
    --workers 4 \
    --rate-limit 100MB/s \
    --resume \
    --verify blake3 \
    --security secure
```

The CLI is intended to provide access to the same core transfer engine used by the graphical interface.

## Graphical Interface

The GUI provides access to DataFlux's transfer engine through an intuitive interface.

A transfer can expose settings such as:

```text
Source:
[ /home/user/Projects ]

Destination:
[ /mnt/backup/Projects ]

Transfer Mode:
[ Automatic ]

Workers:
[ 4 ]

Bandwidth:
[ 100 MB/s ]

Resume:
[ Enabled ]

Verification:
[ BLAKE3 ]

Security:
[ Maximum Security ]

Peer Authentication:
[ Mutual ]

End-to-End Encryption:
[ Enabled ]
```

Advanced settings can be expanded when needed without overwhelming users who simply want to copy a file.

## Transfer Profiles

Frequently used configurations can be saved as profiles.

Example profiles:

```text
Local SSD
Network Backup
Secure Remote
Maximum Throughput
Low Bandwidth
Cellular Transfer
Archive Transfer
Encrypted Backup
```

Profiles can contain settings for:

* Parallelism
* Buffering
* Bandwidth
* Security
* Verification
* Conflict handling
* Network behavior
* Recovery
* Filtering

## Network Awareness

DataFlux can monitor the active network environment.

It can detect or track:

* Network interfaces
* Connection type
* Available bandwidth
* Latency
* Connection quality
* Metered connections
* Connection failures

This allows DataFlux to adapt transfers to changing network conditions.

For example, a transfer can automatically reduce bandwidth usage when operating over a metered cellular connection.

## Recovery

DataFlux is designed to recover from temporary failures whenever possible.

Recovery mechanisms include:

* Automatic retries
* Transfer checkpoints
* Partial-file tracking
* Device reconnection
* Network reconnection
* Interrupted-transfer recovery
* Resume support

Recovery policies can be configured per transfer profile.

## History and Statistics

DataFlux maintains transfer history and statistics so users can review previous operations.

Information can include:

* Transfer duration
* Files transferred
* Bytes transferred
* Average speed
* Peak speed
* Verification results
* Errors
* Retries
* Source
* Destination
* Transfer profile

## Security Philosophy

DataFlux treats security as a layered system.

A secure transfer can involve multiple layers:

```text
Application
    ↓
Transfer Engine
    ↓
Secure Session
    ↓
Authentication
    ↓
Encryption
    ↓
Integrity Protection
    ↓
Network Protocol
    ↓
Storage
```

The exact layers used depend on the selected transfer mode, protocol, and security policy.

DataFlux should prefer established standards and audited cryptographic implementations over custom cryptographic designs.

## Architecture

DataFlux is organized into modular components.

```text
DataFlux
├── Core
├── Filesystem
├── Operations
├── Transfer Engine
├── Parallel Engine
├── Buffering
├── Rate Limiting
├── Conflict Resolution
├── Verification
├── Recovery
├── Storage
├── Networking
├── Protocols
├── Remote Transfers
├── DataFlux Protocol
├── Synchronization
├── Backup
├── Filtering
├── Planning
├── Automation
├── Monitoring
├── Optimization
├── Security
├── Duplicate Detection
├── Analysis
├── History
├── API
├── CLI
├── GUI
└── Platform Integration
```

The architecture is intended to keep individual components replaceable and independently testable.

## Platform Support

DataFlux is intended to support:

* Linux
* Windows
* macOS

Platform-specific functionality is separated from the core transfer engine whenever practical.

## API

DataFlux is designed with an API layer so that other applications can interact with the transfer engine.

Potential API functionality includes:

* Create transfer jobs
* Monitor transfers
* Pause transfers
* Resume transfers
* Cancel transfers
* Modify bandwidth limits
* Retrieve statistics
* Manage profiles
* Retrieve history
* Subscribe to transfer events

## Configuration

DataFlux uses configuration files for persistent settings.

Configuration can cover:

* Transfer profiles
* Network profiles
* Synchronization profiles
* Backup profiles
* Security policies
* Rate-limit rules
* Application preferences

Users can override configuration settings for individual transfers.

## Design Goals

DataFlux is built around several primary goals:

1. **Performance**
   Move data efficiently without blindly consuming system resources.

2. **Reliability**
   Transfers should survive interruptions and recover whenever possible.

3. **Security**
   Sensitive data should have access to strong, standards-based security mechanisms.

4. **Control**
   Users should be able to control how, when, where, and at what speed data moves.

5. **Transparency**
   DataFlux should clearly show what it is doing and why.

6. **Modularity**
   Transfer protocols, storage systems, security mechanisms, and optimization strategies should remain replaceable.

7. **Automation**
   Repetitive transfer, synchronization, and backup tasks should be automatable.

8. **Cross-Platform Support**
   The core transfer engine should work across major desktop operating systems.

## Example Workflow

A secure remote transfer could look like this:

```text
Source Computer
    │
    │ DataFlux Transfer
    │
    ├── Transfer Planning
    ├── File Filtering
    ├── Parallel Scheduling
    ├── Rate Limiting
    ├── Encryption
    ├── Authentication
    ├── Integrity Protection
    └── Resume Checkpoints
            │
            ▼
       Network / Internet
            │
            ▼
       Destination
            │
    ├── Authentication
    ├── Decryption
    ├── Verification
    └── Finalization
```

The user can choose which features are enabled through the transfer interface.

## Example Use Cases

### Local Copy

```text
dataflux copy /home/user/Documents /mnt/backup/Documents
```

### High-Speed Storage Transfer

Use automatic parallelism and buffering to move a large collection of files between SSDs or NVMe drives.

### Secure Remote Transfer

Use DataFlux-to-DataFlux with encrypted communication, mutual authentication, resumability, and integrity verification.

### Low-Bandwidth Transfer

Configure a transfer to remain below a specific bandwidth limit.

### Cellular Transfer

Use a lower bandwidth profile and automatically account for a metered connection.

### Backup

Schedule DataFlux to periodically back up selected directories to another storage device or remote system.

### Synchronization

Create a two-way synchronization job between two directories or systems.

## Project Status

DataFlux is an actively designed open-source project.

The architecture and feature set may evolve as implementation progresses.

Features described as planned or supported in the project documentation may not yet be implemented in every release.

## Development

DataFlux is being developed primarily in Rust.

The project uses a modular architecture so that the core transfer engine can be shared between:

* GUI
* CLI
* API
* Automation
* Remote transfer services
* Platform integrations

## Contributing

Contributions are welcome.

Potential areas for contribution include:

* Transfer engine development
* Filesystem support
* Network protocols
* Performance optimization
* Security
* GUI development
* CLI development
* Platform integration
* Testing
* Documentation
* Benchmarking

When contributing security-sensitive functionality, established standards and well-maintained cryptographic libraries should be preferred over custom implementations.

## License

DataFlux is intended to be released under the GNU General Public License v3.0.

See the repository license for the applicable terms.

## Project Vision

DataFlux is intended to become more than a file-copy utility.

The long-term goal is a unified data movement platform where copying, moving, synchronization, backup, remote transfer, verification, recovery, and secure communication all use the same underlying transfer infrastructure.

Instead of having separate programs for different kinds of data movement, DataFlux provides one configurable engine with the ability to adapt to the user's hardware, network, security requirements, and workflow.
