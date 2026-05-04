const express = require("express");
const app = express();

app.use(express.urlencoded({ extended: true }));

app.get("/", (req, res) => {
  res.send("SERVER OK");
});

app.listen(3000, () => {
  console.log("SERVER PORNIT");
});


const tasks = [];

module.exports = {
  findByUser: (userId) => tasks.filter(task => task.userId === userId),
  create: (task) => {
    tasks.push(task);
    return task;
  },
  delete: (taskId, userId) => {
    const index = tasks.findIndex(t => t.id === taskId && t.userId === userId);
    if (index !== -1) tasks.splice(index, 1);
    return index !== -1;
  },
  updateStatus: (taskId, userId, completed) => {
    const task = tasks.find(t => t.id === taskId && t.userId === userId);
    if (task) task.completed = completed;
    return !!task;
  }
};



vconsole.log("1 - START FILE");

const express = require("express");

console.log("2 - EXPRESS OK");

const app = express();

console.log("3 - APP CREATED");

app.get("/", (req, res) => {
  res.send("OK");
});

console.log("4 - BEFORE LISTEN");



const logger = (req, res, next) => {
  const ip = req.ip || req.connection.remoteAddress || 'unknown';
  console.log(`[${new Date().toISOString()}] ${req.method} ${req.url} - IP: ${ip}`);
  next();
};

module.exports = logger;

module.exports = (req, res, next) => {
  if (!req.session.user) {
    return res.redirect("/login");
  }
  next();
};

app.listen(3000, () => {
  console.log("5 - SERVER PORNIT");
});
