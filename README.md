#### Arrays and Linked Lists Exercise

```js
class Node {
	constructor(val, next=null){
		this.val = val;
		this.next = next;
	}
}

class LinkedList {
	constructor() {
		this.head = null;
		this.tail = null;
	}
	traverse() {
		let currentNode = this.head;
		while(currentNode){
			console.log(currentNode.val);
			currentNode = currentNode.next;
		}
	}
	find(val) {
		let currentNode = this.head;
		while(currentNode){
			if (currentNode.val === val) return true;
			currentNode = currentNode.next;
		}
		return false;
	}
	push(val) { // Appends a new node with the value val to the tail. Returns undefined.
		const newNode = new Node(val);
		if (!this.head){
			this.head = newNode;
			this.tail = newNode;
		}
		this.tail.next = newNode;
		this.tail = newNode;
	}
	unshift(val){ // Add a new node with the valu val to the head. Returns undefined.
		const newNode = new Node(val);
		if (!this.head){
			this.head = newNode;
			this.tail = newNode;
		}
		this.head.next = this.head;
		this.head = newNode;
	}
	pop(){ // Remove and return tail value. Throws error if list is empty.
		// if list is empty, throw error
		let currentNode = this.head;
		if(this.head === null){
			return "ERROR: Empty List"
		}
		for(let i = 0; currentNode.next.next != null; i++){
			currentNode = currentNode.next;
		}
		if(currentNode.next.next === null){ // have two nodes before null
			popped_node = currentNode.next;
			currentNode.next = null;
		}
		return popped_node;
	}
	shift(){ // Remove and return head value. Throws error if list is empty.
		let currentNode = this.head;
		if(!this.head){
			return "ERROR: Empty List"
		}
		shifted_node = currentNode; // temporary head to be returned to user.
		currentNode.next = this.head; // head is now next node over.
		return shifted_node;
	}
	getAt(index){ // Retrieve value at index position 'index'. Throws error if index is invalid.
		let currentNode = this.head;
		for (let i = 0; i < index && currentNode != null; i++){
			currentNode = currentNode.next;
		}
		if(currentNode){
			return currentNode;
		}
		else{
			return "ERROR: Index is invalid";
		}
	}
	setAt(index, val){ // Set value of node at index position 'index' to 'val'. Throws error if index is invalid.
		let currentNode = this.head;
		for (let i = 0; i < index && currentNode != null; i++){
			currentNode = currentNode.next;
		}
		if (currentNode != null){
			currentNode.val = val;
		}
		else{
			return "ERROR: Invalid Index";
		}
	}
	insertAt(index, val){ // Insert a new node at position 'index' with value 'val'. Throws error if index is invalid. Returns undefined.
		let currentNode = this.head;
		let newNode = new Node(val);
		// in instances where we are inserting at the head
		if (index === 0){
			newNode.next = head;
			head = newNode;
		}
		for (let i = 0; i < index && currentNode != null; i++){
			currentNode = currentNode.next;
		}
		if (current != null){
			newNode.next = currentNode.next;
			currentNode.next = newNode;
		}
		else{
			return "Error: Invalid Index";
		}
	}
	removeAt(index){
		let currentNode = this.head;
		// in instances where we are deleting at the head
		if (index === 0){
			head = currentNode.next;
		}
		for (let i = 0; i < index && currentNode != null; i++){
			currentNode = currentNode.next;
		}
		if (currentNode){
			currentNode = currentNode.next;
		}
		else{
			return "ERROR: Invalid Index";
		}
	}
}

```
