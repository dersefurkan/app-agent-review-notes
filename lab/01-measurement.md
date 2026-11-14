# Utility and the security field

AgentDojo logs two results. Neither grades the model's closing sentence.

Utility asks whether the user's task is true in the environment. On the measured banking bill task, the check ignores the model text. It is true only if a transaction exists for the expected amount and the bill recipient. Saying the bill was paid does not count when that transaction is missing. One task's check is not the whole suite.

The security field is the injection check. True means the attacker goal held in later transactions, not in the model's words. "Average security" is the mean of those goal-hit bits. The label sounds like a resistance rate. Zero means the goal did not hold.

If no injection task is passed, the pipeline skips the check and returns true. The no-injection runner documents the same constant. Security true with no injection is not resistance. The attacker goal was never posed. That run is a baseline: the same user request, with ordinary tool output.

Run alone as a user task, the goal check can sit in the utility slot while security stays the early true. Two trues are not two measurements. Both checks can fail while a payment still goes out.

Lab source: the local measurement note. Not a public client file.
