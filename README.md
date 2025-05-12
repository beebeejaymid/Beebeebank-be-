export default function CodeExchange() {
  const [title, setTitle] = useState("");
  const [description, setDescription] = useState("");
  const [code, setCode] = useState("");
  const [submitted, setSubmitted] = useState(false);
  const [credits, setCredits] = useState(0);

  const handleSubmit = (e) => {
    e.preventDefault();
    // Simulate token/credit assignment logic
    const earnedCredits = Math.floor(code.length / 50) + 10;
    setCredits(credits + earnedCredits);
    setSubmitted(true);
  };

  return (
    <div className="p-4 max-w-xl mx-auto bg-white shadow-xl rounded-2xl">
      <h1 className="text-xl font-bold mb-4">Submit Your Code</h1>
      {!submitted ? (
        <form onSubmit={handleSubmit}>
          <input
            className="w-full border p-2 mb-2 rounded"
            placeholder="Title"
            value={title}
            onChange={(e) => setTitle(e.target.value)}
            required
          />
          <textarea
            className="w-full border p-2 mb-2 rounded"
            placeholder="Short Description"
            value={description}
            onChange={(e) => setDescription(e.target.value)}
            required
          />
          <textarea
            className="w-full border p-2 mb-2 rounded font-mono"
            placeholder="Paste your code here..."
            value={code}
            onChange={(e) => setCode(e.target.value)}
            rows={10}
            required
          />
          <button type="submit" className="bg-blue-600 text-white px-4 py-2 rounded">
            Submit Code
          </button>
        </form>
      ) : (
        <div>
          <p className="text-green-600 font-semibold mb-2">
            Code submitted successfully!
          </p>
          <p>You earned <strong>{credits}</strong> credits.</p>
          <button
            className="mt-4 bg-gray-200 px-4 py-2 rounded"
            onClick={() => {
              setSubmitted(false);
              setTitle("");
              setDescription("");
              setCode("");
            }}
          >
            Submit Another
          </button>
        </div>
      )}
    </div>
  );
}
