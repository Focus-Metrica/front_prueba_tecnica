<template>
  <div>
    <nav>
      <a href="#">Navbar</a>
      <button
        type="button"
        data-toggle="collapse"
        data-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span></span>
      </button>

      <div id="navbarSupportedContent">
        <ul>
          <li>
            <a href="#">Home <span>(current)</span></a>
          </li>
          <li>
            <a href="#">Link</a>
          </li>
          <li>
            <a
              href="#"
              id="navbarDropdown"
              role="button"
              data-toggle="dropdown"
              aria-haspopup="true"
              aria-expanded="false"
            >
              Dropdown
            </a>
            <div aria-labelledby="navbarDropdown">
              <a href="#">Action</a>
              <a href="#">Another action</a>
              <div></div>
              <a href="#">Something else here</a>
            </div>
          </li>
          <li>
            <a href="#">Disabled</a>
          </li>
        </ul>
        <form>
          <input type="search" placeholder="Search" aria-label="Search" />
          <button type="submit">Search</button>
        </form>
      </div>
    </nav>
  </div>
</template>
