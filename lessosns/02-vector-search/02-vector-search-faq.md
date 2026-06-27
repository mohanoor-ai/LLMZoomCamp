
## ❓ 1. Why does cosine similarity equal dot product here?

Because the ONNX embedder returns **normalized vectors** (unit length):

```text id="faq1"
||v|| = 1
```

So cosine similarity simplifies to:

```text id="faq2"
cos(a, b) = a · b
```

No manual normalization is needed.

---

## ❓ 2. Why do embeddings need to be used for both query and documents?

Because similarity only works when both are in the **same vector space**:

```text id="faq3"
text → embedding → vector space
```

If query and documents are not embedded the same way, comparison is meaningless.

---

## ❓ 3. Why did I get errors like “could not convert string to float”?

Because a similarity function expected **numeric vectors**, but received raw text.

Wrong:

```text id="faq4"
"# Introduction..."
```

Correct:

```text id="faq5"
embedder.encode(text)
```

Vector search only works on embeddings, not raw strings.

---

## ❓ 4. Why does vector search find results that keyword search misses?

Because vector search uses **meaning**, not exact words.

Example:

```text id="faq6"
"store vectors in PostgreSQL" → matches "pgvector"
```

Even if the word "pgvector" is not in the query.

---

## ❓ 5. Why does hybrid search (RRF) work better than either method alone?

Because it combines two signals:

* Vector search → semantic relevance
* Keyword search → exact matching

RRF ranking:

```text id="faq7"
1 / (k + rank)
```

Documents ranking well in both lists get boosted and win.

---

If you want next, I can turn this into:

* a **1-page revision cheat sheet**
* or a **Module 3 RAG starter notebook (same style, step-by-step)**
