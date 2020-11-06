---
layout: post
title:      "State and Props in Components: Four Questions for Beginners on React.js"
date:       2020-11-06 21:22:53 +0000
permalink:  state_and_props_in_components_four_questions_for_beginners_on_react_js
---

The intention of this blog post is to help a developer build an internal dialogue when first learning to code on the React framework. 

To help better develop critical thinking, here are 4 questions to consider as it pertains to State, Props, and Compontents, both container and presentational:

1. When considering how to optimize a separation of concerns, compare: what is redundant vs. what is reusable?
2. What is the purpose of this component: is it how things look, or how things function?
3. Does this component need to have *state* or can we pass down *props*?
4. Do we need all the methods of a *class*, or will a *function* suffice?

First, if the component is doing both **data-fetching** and **data-rendering**, that might be a bit much. Instead, try doing the fetching in the container, and the rendering in the presentational. This can lead to increased reusability of a compentent receiving different state-sources. Secondly, this approach allows developer to later pinpoint where exactly the UI can be improved. 

Moreover, the container component can be a class with access to state, while the presentational can be a function which receives props. It will look very clean this way, and allow others to follow along with your work-flow.

Here is how my container looks:
```

#./containers/MealFormContainer.js

import React, { Component } from 'react'
import MealCard from '../components/Card/MealCard';
import { connect } from 'react-redux'


class MealsListContainer extends Component {

  constructor(props) {
    super(props)
    this.state = {
      mealFilter: ""
    }
  }

  handleSearch = (e) => {
    this.setState({
      mealFilter: e.target.value
    })

  }

  filterMeals = () => {
    let filteredMeal = this.state.mealFilter.toLowerCase()
    return this.props.meals.filter ((meal) => 
      meal.name.toLowerCase().includes(filteredMeal) || meal.description.toLowerCase().includes(filteredMeal)
    )
  }

  render () {
    if (this.props.loading) {
        return <div>Loading info from backend server...</div>
      }
    else {
      const mealsList = this.filterMeals().map ((meal) => {
        return (

          <div className="col-md-4">
            <MealCard 
            key={meal.id}
            id={meal.id}
            name={meal.name} 
            category={meal.category} 
            description={meal.description}
            imgsrc={meal.image}
            vegan={meal.vegan}
            contains_nuts={meal.contains_nuts}
            contains_dairy={meal.contains_dairy}
            />
          </div>
        )
      })

      return(
        <div>
          <span className="align-middle">
            <h1 className="text-center">All Meals</h1>
            <div className="container-fluid d-flex justify-content-center" >
              <label htmlFor="name">Search by Name: </label>
              <input type="text" id="filter" value={this.state.mealFilter} onChange={this.handleSearch} />
            </div>
          </span>
          <div className="container-fluid d-flex justify-content-center">
            <div className="row">
              { mealsList }
            </div>
          </div>
        </div>
      );
    }
  }
}

const mapDispatchToProps = dispatch => ({
  deleteMeal: id => dispatch ({type: "DELETE_MEAL", id})
})

const mapStateToProps = state => {
  return {
      meals: state.mealsReducer.meals,
      loading: state.mealsReducer.loading
  }
}

export default connect(mapStateToProps, mapDispatchToProps)(MealsListContainer);
```

What's cool about this is that all the functionality is in one place, its got is own state, access to Redux(more on that some other time), and there really isn't much going on in terms of rendering of JSX. 

Meanwhile here's my presentational component:
```
import React from 'react';
import DeleteMealButton from '../Buttons/DeleteMealButton.js'
import MealDescription from './MealDescription.js'
import './card-style.css'


function MealCard (props) {

  return(
    <div className='card text-center shadow' >
      <div className="overflow">
        <img src={props.imgsrc} alt={`${props.name}`} className="card-img-top"/>
      </div>
      <div className="card-body text-dark">
        <h4 className="card-title">
         {props.name}
        </h4>
        <h5 className="card-title">
          {props.category}
        </h5>
        <MealDescription description={props.description} />
        <p className="card-text text-secondary">
          {props.vegan ? "Vegan" : " "}
        </p>
        <p className="card-text text-secondary">
          {props.contains_nuts ? "Contains Nuts" : " "}
        </p>
        <p className="card-text text-secondary">
          {props.contains_dairy ? "Contains Dairy" : " "}
        </p>
        <DeleteMealButton  deleteMeal={props.deleteMeal} id={props.id}/>
      </div>
    </div>
  );
}

export default MealCard;
```

If it becomes necessary to improve how the user views the data, its easier to work right here without being bogged down with other intricacies of functionality. 


Finally:

Quality code requires consistent refractoring. That being said, best practics early in the development stage can create understandable patterns as app development lengthens. Essentially, if something is suppose to simple, but its becoming very complex, step back and reconsider these questions. 

Never forget, the Redux docs are more than a tutorial: they have some pretty cool tips as well. 

If you'd like a litte more reading on class v. functions in React components, this was a great read for me:
[https://hackernoon.com/react-stateless-functional-components-nine-wins-you-might-have-overlooked-997b0d933dbc](http://)


