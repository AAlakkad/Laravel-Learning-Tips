##Login

If you always get Auth::attempts to return false, you probably has created a new User model class, and discarded the already existing class.

When you create/generate a User model and want to use it for login using `Auth::attempt()`, make sure the model class have the following:

* `User` model class must implements `UserInterface` inteface from \Illuminate\Auth\UserInterface, (add `use Illuminate\Auth\UserInterface;` before class declaration).
* `User` model class must have these two methods:

>   public function getAuthIdentifier() {
    	return $this->getKey();
    }
    public function getAuthPassword() {
    	return $this->password;
    }

**Note:** default laravel installation contains a model class named `user` has the above notes.
