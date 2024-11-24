# Project-Management-system
import { useEffect, useState } from "react";
import "./App.css";

function App() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch("http://localhost:8000/users")
      .then((res) => res.json())
      .then((datas) => setData(datas))
      .catch((error) => console.log(error));
  }, []); // Add an empty dependency array to prevent infinite fetch calls

  return (
    <div style={{ padding: "50px" }}>
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>NAME</th>
            <th>EMAIL</th>
            <th>PASSWORD</th>
          </tr>
        </thead>
        <tbody style={{ color: "black" }}>
          {data.map((d, i) => (
            <tr key={i}>
              <td>{d.id}</td>
              <td>{d.name}</td>
              <td>{d.email}</td>
              <td>{d.password}</td>
            </tr>
          ))}
        </tbody>
      </table>
    </div>
  );
}

export default App;


// export default App;
