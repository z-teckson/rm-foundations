# König's Lemma and its equivalence to WKL₀

## Statement of König's Lemma

Let \(T \subseteq \mathbb{N}^{<\mathbb{N}}\) be an infinite, finitely branching tree. That is:
1. \(T\) is a set of finite sequences of natural numbers (nodes) closed under initial segments.
2. For every node \(\sigma \in T\), the set of immediate extensions \(\{\sigma^\frown n : \sigma^\frown n \in T\}\) is finite.
3. \(T\) is infinite as a set of nodes.

**König's Lemma (KL):** Every infinite, finitely branching tree \(T\) has an infinite path.

---

## Equivalence with Weak König's Lemma (WKL₀)

We work over the base system **RCA₀** (Recursive Comprehension with \(\Sigma^0_1\)-induction). The Weak König's Lemma (WKL₀) is the statement:

> Every infinite subtree of \(2^{<\mathbb{N}}\) has an infinite path.

### 1. WKL₀ ⇒ König's Lemma

Assume WKL₀ holds. Let \(T \subseteq \mathbb{N}^{<\mathbb{N}}\) be an infinite, finitely branching tree. We construct a subtree \(S \subseteq 2^{<\mathbb{N}}\) that encodes enough information about \(T\) to apply WKL₀.

**Encoding:** Because \(T\) is finitely branching, each node \(\sigma \in T\) has only finitely many immediate children. Enumerate those children as \(c_0(\sigma), c_1(\sigma), \dots, c_{k_\sigma-1}(\sigma)\). We can fix a recursive enumeration of \(\mathbb{N}^{<\mathbb{N}}\) and use it to assign binary codes to the children. A standard method is to map the tree \(T\) onto a binary tree \(S\) by using a pairing function to represent each child by a block of bits.

More concretely, define a map \(\phi: T \to 2^{<\mathbb{N}}\) such that:
- \(\phi(\varnothing) = \varnothing\).
- If \(\phi(\sigma) = \tau\) and \(\sigma\) has \(m\) children, then for each child \(\sigma^\frown n_i\) we let \(\phi(\sigma^\frown n_i) = \tau^\frown 0^{i}1\) (padded with zeros). This ensures that the images form a finitely branching subtree of \(2^{<\mathbb{N}}\) that is isomorphic to \(T\) up to a bounded branching factor.

Since \(T\) is infinite, the image \(\phi(T)\) is also infinite. Moreover, because the branching is finite, \(\phi(T)\) can be pruned to obtain an infinite subtree \(S \subseteq 2^{<\mathbb{N}}\) that is still infinite. By WKL₀, \(S\) contains an infinite binary path \(p: \mathbb{N} \to \{0,1\}\). Using the inverse of the encoding, we can extract an infinite path through \(T\).

**Formalization in RCA₀:** The construction of \(\phi\) and the verification that it yields an infinite subtree of \(2^{<\mathbb{N}}\) can be carried out with recursive comprehension. The existence of an infinite path in \(S\) given by WKL₀ provides a set \(P\) that is an infinite path. The decoding of \(P\) back to a path in \(T\) is again recursive. Hence, RCA₀ + WKL₀ ⊢ KL.

### 2. König's Lemma ⇒ WKL₀

Now assume König's Lemma holds for all infinite, finitely branching trees. Let \(S \subseteq 2^{<\mathbb{N}}\) be an infinite binary tree (i.e., a subtree of the full binary tree). The binary tree \(S\) is automatically finitely branching (each node has at most two children). Hence \(S\) satisfies the hypotheses of König's Lemma. Applying KL directly yields an infinite path through \(S\).

Thus, over RCA₀, KL implies WKL₀.

---

## Conclusion

Over the base system RCA₀, König's Lemma for infinite, finitely branching trees is equivalent to the Weak König's Lemma (WKL₀). Therefore, König's Lemma belongs to the same reverse‑mathematical strength as WKL₀ and is a member of the “Big Five” systems of second‑order arithmetic.

---
*Formalized in the context of reverse mathematics. This file is part of the `rm‑foundations` collection.*