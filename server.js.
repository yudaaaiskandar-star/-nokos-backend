
const express = require("express");
const cors = require("cors");

const app = express();
const PORT = process.env.PORT || 3000;
const API_TOKEN = process.env.API_TOKEN;

app.use(cors());
app.use(express.json());

function auth(req, res, next) {
  if (!API_TOKEN) {
    return res.status(503).json({
      message: "API_TOKEN belum disetel"
    });
  }

  if (req.headers.authorization !== `Bearer ${API_TOKEN}`) {
    return res.status(401).json({
      message: "Token salah"
    });
  }

  next();
}

app.get("/api/health", (req, res) => {
  res.json({
    status: "ok",
    service: "NOKOS HUB"
  });
});

app.get("/api/orders", auth, (req, res) => {
  res.json({
    orders: [],
    message: "Provider belum dihubungkan"
  });
});

app.post("/api/numbers", auth, (req, res) => {
  res.status(503).json({
    message: "Provider nomor belum dikonfigurasi"
  });
});

app.listen(PORT, () => {
  console.log("NOKOS HUB aktif di port " + PORT);
});
