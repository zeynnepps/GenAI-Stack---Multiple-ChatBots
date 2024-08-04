## Week 11 Homework 3: Optional Project - GenAI Stack - Multiple ChatBots

### Steps to Set Up and Run the Project

#### 1. Clone the GenAI Stack Repository
Open your terminal and run the following command:
```sh
git clone https://github.com/docker/genai-stack.git
```

#### 2. Create a `.env` File
In the project directory, create a `.env` file with the following content:
```env
OPENAI_API_KEY=your_api_key
NEO4J_URI="neo4j+s://AURADB-INSTANCE:7687"
NEO4J_USERNAME=neo4j
NEO4J_PASSWORD=password
NEO4J_DATABASE=neo4j
LLM=gpt-4
EMBEDDING_MODEL=openai
```

#### 3. Start Docker Containers
Open the Docker app on your computer and run the following command in the terminal:
```sh
docker compose up
```
This command will download (at the first run) and start all containers in dependency order.

#### 4. Access the Application
Open your browser and navigate to:
- [http://localhost:8502](http://localhost:8502)
- [http://localhost:8505](http://localhost:8505)

#### 5. Install Neo4j
Install Neo4j using Homebrew:
```sh
brew install neo4j
```

#### 6. Start Neo4j
Start the Neo4j service:
```sh
neo4j start
```

#### 7. Run Sample Queries in Neo4j
Open the Neo4j browser and execute the following sample queries:
```cypher
// Create some sample nodes and relationships
CREATE (a:Person {name: 'Alice', age: 30})
CREATE (b:Person {name: 'Bob', age: 25})
CREATE (c:Person {name: 'Charlie', age: 35})

CREATE (a)-[:FRIENDS_WITH]->(b)
CREATE (b)-[:FRIENDS_WITH]->(c)
```

#### 8. Create a Python Script to Connect to Neo4j
Create a file named `connect_neo4j.py` with the following content:
```python
from neo4j import GraphDatabase

# Set up the Neo4j connection parameters
uri = "bolt://localhost:7687"
username = "neo4j"
password = "your_password"  # Replace with your actual password

# Create a driver instance
driver = GraphDatabase.driver(uri, auth=(username, password))

def query_neo4j():
    with driver.session() as session:
        result = session.run("MATCH (n) RETURN n LIMIT 10")
        for record in result:
            print(record)

if __name__ == "__main__":
    query_neo4j()
```

#### 9. Run the Python Script
Execute the script to connect to Neo4j and run a sample query:
```sh
python connect_neo4j.py
```

---
