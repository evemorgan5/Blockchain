# Blockchain
Understanding Blockchain technology 
from datetime import datetime as dt 
import hashlib
import json

class Blockchain:
    def __init__(self):
        self.blocks = [Block(0, "0")]
        
    def add_block(self, block):
        self.blocks.append(block)
        return None
    
    
class Block:
    def __init__(self, amount, previous_hash=None):
        self.timestamp = dt.now().strftime("%Y-%m-%d %H:%M:%S")
        self.amount = amount 
        self.previous_hash = previous_hash
        self.current_hash = self.compute_current_hash()
        
    def compute_current_hash(self):
        data = (str(self.timestamp) + str(self.amount) + str(self.previous_hash))
        current_hash = hashlib.sha256(data.encode("utf-8")).hexdigest()
        return current_hash
        
        
blockchain = Blockchain()
print(blockchain.blocks[0])
