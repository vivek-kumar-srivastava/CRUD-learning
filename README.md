# CRUD-learning
making todo list to learn crud in nextJS
code:


'use client'
import { useState } from "react";

export default function Home() {
  const [task, setTask] = useState(["Assignments","Gym","Nap"]);
  const [newtask, setNewtask] = useState("");
  const AddTask = ()=>{
    if(newtask.trim() != ""){
      setTask(prevState=>[...prevState,newtask]);
      setNewtask("")
    }
  }
  const DeleteTask=(index)=>{
       const updatedTask = task.filter((_,i)=> i!== index );
      setTask(updatedTask);
  }
  
  return (
    <>
    <div className=" mt-24 items-center justify-items-center font-[family-name:var(--font-geist-sans)]">
      <h1>To-Do List</h1>
      <div className="mt-6 mb-6">
      <input
          className="text-black bg-grey border-blue-200 rounded"
          type="text"
          placeholder="Create Task"
          value={newtask}
          onChange={(e) => setNewtask(e.target.value)}
        />
        <button className=" ml-2 bg-green-600 px-2 py-0 rounded" 
        onClick = {AddTask}>
        Add Task
        </button>
        </div>
      <div>
      <ol>
      {task.map((val,index) => {
   return (<div className="flex items-center m-5 justify-between p-1 w-80 bg-blue-600 rounded">
   <li className="truncate" key={index}><span>{val}</span></li>
   
   <button className="ml-auto mr-2 text-white bg-red-600 px-2 py-0 rounded"
   onClick={()=>DeleteTask(index)}
   >Delete</button>
 </div>

 
   )
        }) 
      }
</ol>
        </div>
     
    </div>
    </>
  );
}
