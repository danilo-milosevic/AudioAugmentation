## 6.4 Naučene augmentacije korišćenjem neuronskih mreža

Problem kod svih prethodnih metoda augmentacije je bila potreba za ručnim definisanjem pravila kako augmentisati podatke. Umesto ručne augmentacije, moguće je naučiti modele da generišu nove podatke (generativni modeli kao što su GAN-ovi, autoencoderi itd.) ili definisanjem mogućih augmentacija nakon čega model uči kako kombinovati augmentacije da bi model ostvario bolje rezultate preko reinforcement learning-a

### 6.4.1 AutoAugment

Opisan u Google-ovom radu iz 2019 godine, predstavlja reinforcement learning metodu koja uči kako kombinovati augmentacije tako da model ostvari bolje performanse. Iako prvenstveno razvijan za slike, moguće je primeniti i na audio podacima.

Princip rada je sledeći

1. **Inicijalizacija**

    U prvom koraku se incijalizuje, odnosno definiše *search space* augmentacija što predstavlja sve moguće augmentacije koje agent može primeniti nad podacima kao i njihove parametre. Cilj agenta je pronaći u tom prostoru augmentacija najbolje kombinacije.

2. **Predlaganje politike**

    U sledećem koraku reinforcement learning agent predlaže *augmentation policy*, tj politiku augmentacije, što predstavlja kombinaciju augmentacija i parametara.

3. **Trening modela**

    Koristeći predloženu politiku augmentacije, model se trenira sa augmentisanim skupom podataka i mere se performanse tako dobijenog modela.

4. **Ažuriranje agenta**

    Mere se performanse modela treniranog sa primenjenom politikom i rezultati se koriste kao nagrade (*reward*) za reinforcement learning agenta. Na ovaj način, kroz iteracije, agent uči koje augmentacije najbolje utiču na performanse modela-


\begin{figure}[ht]
\centering
\includegraphics[width=8cm]{figures/6_advanced_augm/autoaugment.jpg}
\caption{AutoAugment kod slika}
\label{fig:autoaugment}
\end{figure}