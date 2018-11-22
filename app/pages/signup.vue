<template>
  <div data-page="sign-up" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="back link icon-only" href="#"><i class="icon icon-back"></i></a></div>
        <div class="center">Sign Up</div>
      </div>
    </div>
    <div class="page-content">
      <div class="content-block-title"></div>
      <form class="list-block inputs-list">
        <ul>
          <li>
            <div class="item-content">
              <div class="item-media"><i class="icon material-icons"></i></div>
              <div class="item-inner">
                <div class="item-title floating-label">Your name</div>
                <div class="item-input">
                  <input type="text" placeholder="">
                </div>
              </div>
            </div>
          </li>
          <li>
            <div class="item-content">
              <div class="item-media"><i class="icon material-icons"></i></div>
              <div class="item-inner">
                <div class="item-title floating-label">E-mail</div>
                <div class="item-input">
                  <input type="email" placeholder="">
                </div>
              </div>
            </div>
          </li>
          <li>
            <div class="item-content">
              <div class="item-media"><i class="icon material-icons"></i></div>
              <div class="item-inner">
                <div class="item-title floating-label">Password</div>
                <div class="item-input">
                  <input type="password" placeholder="">
                </div>
              </div>
            </div>
          </li>
          <li>
            <div class="item-content">
              <div class="item-media"><i class="icon material-icons"></i></div>
              <div class="item-inner">
                <div class="item-title floating-label">Gender</div>
                <div class="item-input">
                  <select>
                    <option> </option>
                    <option>Male</option>
                    <option>Female</option>
                  </select>
                </div>
              </div>
            </div>
          </li>
          <li>
            <div class="item-content">
              <div class="item-media"><i class="icon material-icons"></i></div>
              <div class="item-inner">
                <div class="item-title label">Birth date</div>
                <div class="item-input">
                  <input type="date" placeholder="Birth day" value="2014-04-30">
                </div>
              </div>
            </div>
          </li>
        </ul>
        <div class="content-block">
          <p class="buttons-row"><a href="/home/" class="button button-raised">Submit</a></p>
        </div>
      </form>
    </div>
  </div>
</template>
