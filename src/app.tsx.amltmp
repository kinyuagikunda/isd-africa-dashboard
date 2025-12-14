import { useEffect, useState } from "react";
import { API_BASE_URL } from "./api";

function App() {
  const [countries, setCountries] = useState<string[]>([]);
  const [country, setCountry] = useState<string>("");
  const [error, setError] = useState<string>("");

  useEffect(() => {
    async function load() {
      try {
        setError("");
        const res = await fetch(`${API_BASE_URL}/countries`);
        if (!res.ok) throw new Error(`HTTP ${res.status}`);
        const data = await res.json();
        setCountries(data.countries || []);
      } catch (e: any) {
        setError(e?.message || "Failed to load countries");
      }
    }
    load();
  }, []);

  return (
    <div style={{ padding: "1rem", fontFamily: "sans-serif" }}>
      <h1>Africa ISD Dashboard</h1>

      {error && (
        <div style={{ padding: "0.5rem", background: "#fee", marginBottom: "1rem" }}>
          Error: {error}
        </div>
      )}

      <label style={{ display: "block", marginBottom: "0.5rem" }}>
        Country:
      </label>
      <select
        value={country}
        onChange={(e) => setCountry(e.target.value)}
        style={{ padding: "0.5rem", minWidth: 260 }}
      >
        <option value="">-- Select --</option>
        {countries.map((c) => (
          <option key={c} value={c}>
            {c}
          </option>
        ))}
      </select>

      <p style={{ marginTop: "1rem" }}>
        Loaded countries: <b>{countries.length}</b>
      </p>
      <p>
        Selected: <b>{country || "(none)"}</b>
      </p>
    </div>
  );
}

export default App;
