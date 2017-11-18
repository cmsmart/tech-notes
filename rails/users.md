# Users and Profiles

### Create user regisration with devise

``` rails g devise User ```


### Create profile


``` rails g scaffold Profile username first_name last_name user:references avatar_data:text ```

#### Ensure username is unique in migration file  e.g

```
class CreateProfiles < ActiveRecord::Migration[5.1]
  def change
    create_table :profiles do |t|
      t.references :user, foreign_key: true
      t.string :username
      t.string :name
      t.text :bio

      t.timestamps

      # No one can have the same username
      t.index :username, unique: true
    end
  end
end

```

#### In profiles controller 

* Make user set up their profile page if they haven’t yet

```
def show
    redirect_to edit_profile_url if @profile.nil?
end

```

* Authenticate user

```  before_action :authenticate_user!, only: [:edit, :update, :destroy]```

* Have blank profile for form if the user hasn’t created one yet for their account
```
  def edit
    @profile = Profile.new(user: current_user) if @profile.nil?
  end
  ```
* Def create
```
  def create
    @profile = Profile.new(profile_params)
    @profile.user = current_user
    ```

* Set set_profile method params
```
    # Use callbacks to share common setup or constraints between actions.
    def set_profile
      if params[:id]
        # A particular person’s profile page
        # e.g. /users/5
        @profile = Profile.find_by!(user_id: params[:id])
      else
        # The signed in user’s profile page
        # /profile
        @profile = Profile.find_by(user: current_user)
      end
    end
```

* Change update method
```
  def update
    respond_to do |format|
      if @profile.nil? || @profile.user != current_user
        redirect_to root_url
      elsif @profile.update(profile_params)
        format.html { redirect_to @profile, notice: 'Profile was successfully updated.' }
        format.json { render :show, status: :ok, location: @profile }
      else
        format.html { render :edit }
        format.json { render json: @profile.errors, status: :unprocessable_entity }
      end
    end
  end
  ```

  In user.rb

  * restrict to one profile
  ``` has_one :profile```

  NEED A REDIRECT TO PROFILE AFTER SIGN UP