# **Budget MDP** 



<!-- Start of picture text -->
(0,4)so A0—> Rt, $1 A1—> R2, $2 A2—> 3, $3 AB (ee)R4, Sh<br><!-- End of picture text -->

- S0: state at time 0 (initial state) = (money, weeks_left) = (0, 4) 

- A0: action at time 0, spend or save 

- R1, S1: reward and state at time 1 

- and so on until time T = 4, when weeks_left = 0 and the episode ends 

## **Design details** 

**State:** (money, weeks_left), starting at (0, 4) 

- money: 0 to 6 (my saved money) 

- weeks_left: 4 down to 0 

**Actions:** spend, save 

- spend: the 2 euro are gone, I get fun 

- save: money goes up by 2 

**Transition:** There is a 40% chance of an unexpected cost of 3 appearing. If i have 3 or more in my money you pay the cost. If i dont have enough i go into debt and my money becomes 0. 

### **Reward** 

**Part Value** fun +1 for spending (0.5 per euro) debt -4 if a bill arrives and I cannot pay it savings_left +1 per euro left at the end 

**End:** when weeks_left is 0. 

**Trade-off:** fun now (spend) against safety and a bigger end reward (save). 

## **How I think it behaves** 

- Always spend should do badly 

- Always save should be safe but gives no fun. 

- A mix should be best: save first, spend when I already have enough for a bill. 

## **Parameters and what I expect** 

- Chance of a surprise cost (40%): if it goes up, saving matters more. If it goes down, spending is less risky. 

- Size of the cost (3): a bigger cost needs a bigger buffer, so I would have to save for more weeks before spending. 

- Fun for spending (+1): if it goes up, spending becomes more attractive. 

- Debt penalty (-4): if it gets smaller, going into debt hurts less and saving is less needed. 

- Value of money left at the end (+1 per euro): if it goes down, saving loses its reward at the end. 

## **Process:** 

I chose a scenario I could relate to: Budgeting. 

1. 2 actions were needed (Spend and Save), along with 1 money value. 

2. Weeks left was added to give the budget a finishing point. A reward was added at the end of the month for having money left. 

3. A random surpise cost was added so there was a reason to save, and it meant that the results would not always be the same. 

4. The process, states, actions, transitions and rewards were put into a list like the slides explain for an MDP. 

## **What works and what does not work yet** 

### **What works (on paper):** 

- Two numbers in the state and two actions. (small code) 

- There is a real trade-off = fun now against safety later. 

**What does not work yet:** 

- I have no code yet, so nothing has been tested and my predictions above are only guesses. 

- I do not know yet which plan is best. 

- Saving 2 euro in week 1 does not protect me from a cost of 3, which might feel unfair. 

- Only one random event (the surprise cost) and one kind of cost. 

