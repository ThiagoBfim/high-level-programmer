# 5 Tips to become a better programmer

If you are a programmer, or want to become one, I will give you 5 tips to help you improve your career.

### Be analytic

You have to analyze the tasks, thinking about the future and the end user. This helps you to identify betters solutions.

If someone asks you for a feature, understand why it exists, what it is for, and who the users will be. Here it would help if you were empathetic, you are responsible for changing other people's lives through software.

Example:

New functionality is requested to create users. This functionality must have only email and password.

**Solution without analysis:** A simple form with e-mail, password, and a button to submit the form and save the data in a SQL Database.

**Solution with analysis:** A simple form, with e-mail, password, and password validation to have enough characters to be safe, and a button to submit the form and save it in the SQL Database. But the password will have cryptography to protect the user's data.

It is extremely important to think analytically to suggest to the customer the improvements that are necessary for a professional product.

### Know how to read (ugly code) and write code (clean code)

80% of what you're going to do is read code

You need to know how to write clean code, but most code you write is ugly, and you need to know how to read it.

Example:

```
Car update(Long id){
  Carro c = repository.findById(id);
  return repository.save(c);
}
```

You need to know how to read this code and explain it in a simple sentence.

In this example, the method should find a car and create or update if the car already exists.

After reading this method, we may notice that it is not clear enough. The method name is updated, but if the car doesn't exist it will throw an exception, is it expected?

### Keep training

There is no professional without training.\
Kobe Bryant didn't turn pro without training.\
Cristiano Ronaldo did not turn professional without training.\
You will not become a professional without training.\
You must always be practicing to always do better.

> Practice, Practice, Practice. True professionals keep their skills sharp and ready. Musicians don't get better by performing(doing your job), they get better by practicing (outside of work). The same rules applies to engineers.

\- Robert Cecil Martin

I recommend the channel of the Brazilian Alberto Souza on Youtube, to learn more about it, visit: https://www.youtube.com/channel/UC9xYzttzFxK9cmhKPQCalYQ

### Be updated

You need to be always up to date, the world of technology is constantly evolving, and you need to be too.

If you don't keep up with the main technologies you work on and would like to work on in the future, you will become outdated and become a bad programmer.

> To the man with only a hammer, every problem looks like a nail.

To keep updated, you can find groups, for example JUG(Java User Group) for Java, or any kind of IT group.

Another way is to use Twitter and follow person that work with things you use, or want to know more about it.

### Be professional

If what you do with whimsy, with real interest, then you're probably not being professional.

What you do impacts other people's lives, so be responsible for what you produce.

> In one way or another, all professionals practice. They do this because they care about doing the best job they possibly can. What’s more, they practice on their own time because they realize that it is their responsibility—and not their employer’s—to keep their skills sharp. Practicing is what you do when you aren’t getting paid. You do it so that you will be paid, and paid well.

\- Robert Cecil Martin

### Conclusion

If you follow these tips, definitely you will be a better professional, and will be able to create better code, and be more satisfaction.

Even though, these are just 5 tips, in every tip you should learn deep to get better.

Now it's your turn to deepen this knowledge, to evolve more and more 😃

### References

**Clean code: A Code of Conduct for Professional Programmer**\
\- Robert Cecil Martin
