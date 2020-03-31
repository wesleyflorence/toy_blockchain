# Toy Blockchain

## How to play
__Start a node__  
`python3 blockchain.py <PORT>`

__Mine__  
Assuming were running our node locally on port 5000 you can mine a block with a GET request at http://localhost:5000/mine

__Chain__  
View the current state of the chain at http://localhost:5000/chain

__Transaction__  
Add a new transaction with a post request:
```
❯ curl -X POST -H "Content-Type: application/json" -d '{
"sender": "wes",
"recipient": "philly",
"amount": 5
}' "http://localhost:5000/transactions/new"
```

__Register a New Node__  
Start a new node on a different port or on a differnt machine with
`python3 blockchain.oy <PORT>`.  
For this example we start a new node at http://localhost:8080


To register our original node make a post request:
```
❯ curl -X POST -H "Content-Type: application/json" -d '{
"nodes": ["http://localhost:5000"]
}' "http://localhost:8080/nodes/register"
```

__Consensus__  
Now make a GET request to http:localhost:8080/nodes/resolve to acheive consensus.  
Check to make sure at http:localhot:5000/chain
