**Absolute Track**  - Subract if point is blow the line or add if point is above the line

![image](https://user-images.githubusercontent.com/92245436/147322936-0b746cef-bfaf-4a50-aace-957d032f00b5.png)

**Square Track**

![image](https://user-images.githubusercontent.com/92245436/147323410-f807890e-59fc-45ff-aea2-3ed2a9bd584f.png)

**Gradient Descent**

![image](https://user-images.githubusercontent.com/92245436/147324668-cbdfdc6c-beec-46bc-8b3e-4247a3d35a80.png)

**Mean Absolute Error**

![image](https://user-images.githubusercontent.com/92245436/147324917-528a6b37-5618-4378-b27f-d5989c03a30b.png)

**Mean Squared Error**

![image](https://user-images.githubusercontent.com/92245436/147325057-40fb5200-0a2b-40e6-b887-9556d832a64c.png)

![image](https://user-images.githubusercontent.com/92245436/147325856-c66a40d8-1e24-4eab-9e73-895479a5eb28.png)

#### Mean vs Total Squared (or Absolute) Error
A potential confusion is the following: How do we know if we should use the mean or the total squared (or absolute) error?
![image](https://user-images.githubusercontent.com/92245436/147326512-bd8de930-be0c-4d4e-a59a-589b3e315f9a.png)


#### Batch vs Stochastic Gradient Descent
At this point, it seems that we've seen two ways of doing linear regression.

- By applying the squared (or absolute) trick at every point in our data one by one, and repeating this process many times.
- By applying the squared (or absolute) trick at every point in our data all at the same time, and repeating this process many times.
More specifically, the squared (or absolute) trick, when applied to a point, gives us some values to add to the weights of the model. We can add these values, update our weights, and then apply the squared (or absolute) trick on the next point. Or we can calculate these values for all the points, add them, and then update the weights with the sum of these values.

The latter is called batch gradient descent. The former is called stochastic gradient descent.
![image](https://user-images.githubusercontent.com/92245436/147326742-4480a818-04f8-48ee-99ce-2a5b83166abb.png)

#### Closed form solution math
![image](https://user-images.githubusercontent.com/92245436/147329193-e2de8c04-1424-4159-a7b1-fbcb555a874e.png)
![image](https://user-images.githubusercontent.com/92245436/147329231-283decfa-ea50-41bd-ad85-d25f47753348.png)
![image](https://user-images.githubusercontent.com/92245436/147329290-db851ab4-ad07-41bb-b206-5910c4b42ba0.png)
![image](https://user-images.githubusercontent.com/92245436/147329374-a191de5a-cd61-43b7-9090-e781f5278c4e.png)
![image](https://user-images.githubusercontent.com/92245436/147329401-c98c66ba-9d1a-4857-aa55-f0d788d50d96.png)
![image](https://user-images.githubusercontent.com/92245436/147329499-5d289c69-b1f9-4f36-9eed-9f5e75d1ebbf.png)



