# Steps for the Android Jetpack ViewModel Demo
ViewModel is a pre-requisite for using LiveData

## Steps
* Create a project using the Fragment + ViewModel template.
* The template creates a single activity to hold all subsequent Fragments
* A Content Fragment is created that uses the FrameLayout to hold Fragments
* Fragments use a FragmentManager class to assist in attaching to Activities
* We populate the ViewModel class with variables we'd like to use in the App
* MainFragment will behave like ActivityMain did
* Draw the UI (Figure 39-3)
* Implement the ViewModel:
package com.ebookfrenzy.viewmodeldemo.ui.main
import androidx.lifecycle.ViewModel
class MainViewModel : ViewModel() {
    private val usd_to_eu_rate = 0.74f
    private var dollarText = ""
    private var result: Float = 0f

    fun setAmount(value: String) {
        this.dollarText = value
        result = value.toFloat() * usd_to_eu_rate
    }

    fun getResult(): Float? {
        return result
    }
}
* Associate the Fragment with the ViewModel:
val viewModel = ViewModelProviders.of(this).get(MainViewModel::class.java)
* Implement an event handler to interact with the data stored in ViewModel
** This can only be done in code and not in the Layout XML file
## Live Data
We can add a LiveData as a component to the ViewModel

* Update ViewModel consistent with the example in section 40.2
* Implement Observer class