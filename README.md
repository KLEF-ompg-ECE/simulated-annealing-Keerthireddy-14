# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

**Student Name  :** Toorpu Keerthi Reddy
**Student ID    :** 2310040068  
**Date Submitted:** 25 march 2026  

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `sa_timetable.py` and read through it. Then answer these questions.

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**

```
[count_clashes() measures the number of conflicts in the timetable, where exams that should not be scheduled together are placed in the same slot. It counts how many such clashes occur. A perfect timetable has 0 clashes, meaning no conflicting exams are scheduled at the same time.]
```

**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**

```
[generate_neighbor() creates a new timetable by making a small random change to the current timetable, such as moving a subject from one slot to another. This helps explore nearby possible solutions. The new timetable is slightly different but still similar to the current one.]
```

**Q3. In `run_sa()`, there is this line:**
```python
if delta < 0 or random.random() < math.exp(-delta / T):
```
**What does this line decide? Why does SA sometimes accept a worse solution?**

```
[This line decides whether to accept the new solution or not. If the new solution is better (delta < 0), it is always accepted. If it is worse, it may still be accepted with a probability based on temperature, which helps the algorithm escape local minima and explore better solutions.]
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python sa_timetable.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of iterations completed |1379|
| Clashes at iteration 1 |12|
| Final best clashes |3|
| Did SA reach 0 clashes? (Yes / No) |No|

**Copy the printed timetable output here:**
```
[Slot 1: Geography
Slot 2: Chemistry, English
Slot 3: History, Computer Science, Economics
Slot 4: Biology, Statistics
Slot 5: Mathematics, Physics

Total clashes : 3]
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest drop in clashes happen? Does the curve flatten out?*
```
[The graph shows a sharp decrease in clashes at the beginning, indicating rapid improvement in the early stages. After that, the curve gradually flattens, showing slower improvement as the algorithm converges. The biggest drop happens in the initial iterations, and later changes are minimal.]
```

---

## Experiment 2 — Effect of Cooling Rate

**Instructions:** In `sa_timetable.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `cooling_rate` = **0.80**, **0.95**, and **0.995**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
|-------------|---------------|----------------------|--------------------|
| 0.80        |      8         |        31              |      No              |
| 0.95        |       3        |        135              |       No             |
| 0.995       |       3        |        1376              |        No            |

**Compare the three plots. What do you notice about how fast vs slow cooling affects the result? (3–4 sentences)**  
*Hint: Fast cooling = temperature drops quickly. Does it have time to explore well?*
```
[With a fast cooling rate (0.80), the algorithm stops quickly and gives a poor solution because it does not explore enough. With moderate cooling (0.95), it performs better by balancing exploration and convergence. With slow cooling (0.995), the algorithm explores more thoroughly and achieves a good solution, but takes more iterations. Overall, slower cooling leads to better results but requires more time.]
```

**Which cooling_rate gave the best result? Why do you think that is?**
```
[The best result was obtained with cooling_rate = 0.995 because it allowed the algorithm to explore more solutions before converging. This increases the chances of finding a near-optimal timetable. Although it takes more iterations, it provides a better and more stable solution.]
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final clashes | Main finding in one sentence |
|------------|-------------|---------------|------------------------------|
| 1 — Baseline | cooling_rate = 0.995 |3|Slow cooling gives stable and improved solutions over time. |
| 2 — Cooling rate | cooling_rate = ___ |3|Slower cooling provides better results than fast cooling. |

**In your own words — what is the most important thing you learned about Simulated Annealing from these experiments? (3–5 sentences)**
```
[The most important thing I learned is that temperature and cooling rate play a crucial role in Simulated Annealing. A high temperature allows the algorithm to explore many solutions, while a slow cooling rate helps in gradually refining the solution. If cooling is too fast, the algorithm may get stuck in a poor solution. If it is slow, it finds better solutions but takes more time. Thus, choosing the right balance is important for optimal performance.]
```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, timetable pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
