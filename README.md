# DAGenie

## Purpose-Built for DAGs. Engineered for Speed.

Dagenie is a high-performance, distributed database purpose-built to manage Directed Acyclic Graphs (DAGs). With disk persistence via BadgerDB, clustered storage with sharding, replication, and a powerful query language (DQL), Dagenie empowers developers and system architects to build, manage, and introspect complex DAG workflows at scale.

---

## Features

- ✨ **DAG-First Design**: Optimized for storing and querying DAG structures.
- 🔢 **Disk Persistence**: Leveraging BadgerDB for high-speed, embedded storage.
- 🛡️ **Raft Consensus**: Strong consistency, replication, and leader election.
- 📊 **Sharded Storage**: Scalable horizontal partitioning via consistent hashing.
- 📊 **Replication**: Configurable replication factor with quorum writes/reads.
- ⚙️ **gRPC & TCP Interfaces**: Dual interfaces for custom app integration.
- 🔍 **DQL Query Language**: Custom query language with WHERE, UPDATE, DELETE, COMMIT, ROLLBACK.
- 🔎 **Full-Text Indexing**: Fast indexed DAG and task lookup.
- 🔄 **Gossip Protocol**: Cluster discovery, failure detection, auto-rebalancing.
- 🤑 **User Privileges**: Admin/user roles with scoped permissions.

---

## Getting Started

### 🔧 Installation

```bash
git clone https://github.com/aboyai/dagenie.git
cd dagenie
go build -o dagenie main.go
```

### 🔍 Running Dagenie

```bash
./dagenie --config config.yaml
```

### 🔍 Creating a DAG via CLI

```bash
./dagenie create-dag --id mydag
./dagenie add-task --dag mydag --id T1 --payload '{}' --depends []
./dagenie query-dag --dag mydag
```

---

## Folder Structure

```
dagenie/
├── cluster/
│   ├── storage/            # BadgerDB FSM
│   │   └── storage.go
│   ├── raftnode/
│   │   ├── raft.go         # Raft init & FSM binding
│   │   └── fsm.go          # FSM logic for DAG
│   └── gossip/             # Gossip cluster management
│       └── gossip.go
├── query/
│   ├── dql/                # Participle grammar & parser
│   ├── executor.go         # DQL execution
│   └── planner.go          # Query plan caching
├── connector/
│   └── tcp/
│       └── server.go       # TCP interface
├── proto/
│   └── dagenie.proto       # gRPC interface
├── clients/                # Multilingual client libs
│   ├── go/
│   ├── java/
│   ├── python/
│   ├── nodejs/
│   ├── cpp/
│   ├── rust/
│   ├── dotnet/
│   └── ruby/
├── config.yaml
├── main.go
└── README.md
```

---

## Configuration (config.yaml)

```yaml
node_id: node-1
bind_addr: 127.0.0.1:9000
data_dir: ./dagenie/storage
raft:
  bind_addr: 127.0.0.1:7000
  join_addresses:
    - 127.0.0.1:7001
replication:
  factor: 3
quorum:
  read: 2
  write: 2
sharding:
  virtual_nodes: 128
```

---

## DQL Syntax

```sql
SELECT * FROM dag WHERE id = 'mydag';
UPDATE task SET payload = '{"key": "val"}' WHERE id = 'T1';
DELETE FROM task WHERE id = 'T2';
COMMIT;
ROLLBACK;
```

---

## Language Clients

- [Go Client](./clients/go/README.md)
- [Java Client](./clients/java/README.md)
- [Python Client](./clients/python/README.md)
- [Node.js Client](./clients/nodejs/README.md)
- [C++ Client](./clients/cpp/README.md)
- [Rust Client](./clients/rust/README.md)
- [.NET Client](./clients/dotnet/README.md)
- [Ruby Client](./clients/ruby/README.md)

---

## Contributing

We welcome contributions! Please submit issues and pull requests.

- [Contribution Guide](./CONTRIBUTING.md)
- [Code of Conduct](./CODE_OF_CONDUCT.md)

---

## License

MIT License © 2025 Aboyai LLC

---

## Contact & Support

For enterprise support, integration help, or queries:

- Email: [support@dagenie.io](mailto\:support@dagenie.io)
- Website: [https://dagenie.io](https://dagenie.io)

---

*Dagenie — Purpose-Built for DAGs. Engineered for Speed.*

