---
Created: 22:54 26-10-2023
tags:
  - project
---

# HandleForm
```jsx
import React, { useState } from "react";
import "bootstrap/dist/css/bootstrap.css";

export default () => {
  const [formState, setFormState] = useState({
    formValues: {
      email: "",
      password: ""
    },
    formErrors: {
      email: "",
      password: ""
    },
    formValidity: {
      email: false,
      password: false
    }
  });

  const handleChange = ({ target }) => {
    const { formValues } = formState;
    formValues[target.name] = target.value;
    setFormState({ formValues });
    handleValidation(target);
  };

  const handleValidation = target => {
    const { name, value } = target;
    const fieldValidationErrors = formState.formErrors;
    const validity = formState.formValidity;
    const isEmail = name === "email";
    const isPassword = name === "password";
    const emailTest = /^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/i;

    validity[name] = value.length > 0;
    fieldValidationErrors[name] = validity[name]
      ? ""
      : `${name} is required and cannot be empty`;

    if (validity[name]) {
      if (isEmail) {
        validity[name] = emailTest.test(value);
        fieldValidationErrors[name] = validity[name]
          ? ""
          : `${name} should be a valid email address`;
      }
      if (isPassword) {
        validity[name] = value.length >= 3;
        fieldValidationErrors[name] = validity[name]
          ? ""
          : `${name} should be 3 characters minimum`;
      }
    }

    setFormState({
      ...formState,
      formErrors: fieldValidationErrors,
      formValidity: validity
    });
  };

  const handleSubmit = event => {
    event.preventDefault();
    const { formValues, formValidity } = formState;
    if (Object.values(formValidity).every(Boolean)) {
      // Form is valid
      console.log(formValues);
    } else {
      for (let key in formValues) {
        let target = {
          name: key,
          value: formValues[key]
        };
        handleValidation(target);
      }
    }
  };

  return (
    <div className="container">
      <div className="row mb-5">
        <div className="col-lg-12 text-center">
          <h1 className="mt-5">React regular form</h1>
        </div>
      </div>
      <div className="row">
        <div className="col-lg-12">
          <form onSubmit={handleSubmit}>
            <div className="form-group">
              <label>Email address</label>
              <input
                type="email"
                name="email"
                className={`form-control ${
                  formState.formErrors.email ? "is-invalid" : ""
                }`}
                placeholder="Enter email"
                onChange={handleChange}
                value={formState.formValues.email}
              />
              <div className="invalid-feedback">
                {formState.formErrors.email}
              </div>
            </div>
            <div className="form-group">
              <label>Password</label>
              <input
                type="password"
                name="password"
                className={`form-control ${
                  formState.formErrors.password ? "is-invalid" : ""
                }`}
                placeholder="Password"
                onChange={handleChange}
                value={formState.formValues.password}
              />
              <div className="invalid-feedback">
                {formState.formErrors.password}
              </div>
            </div>
            <button type="submit" className="btn btn-primary btn-block">
              Submit
            </button>
          </form>
        </div>
      </div>
    </div>
  );
};
```






--- 
# References
[React Hook Form - xử lý form dễ dàng hơn bao giờ hết (viblo.asia)](https://viblo.asia/p/react-hook-form-xu-ly-form-de-dang-hon-bao-gio-het-RnB5pAdDKPG)
[(1) React Hook Form VS Formik (viblo.asia)](https://viblo.asia/p/react-hook-form-vs-formik-Qbq5QmwR5D8)
[useFieldArray (react-hook-form.com)](https://react-hook-form.com/docs/usefieldarray)
[Using yup and typescript for typesafe select validation | by Daniel Voigt | Medium](https://yidaotus.medium.com/using-yup-and-typescript-for-typesafe-select-validation-e9ee9d4bceec)

--- 
# Links to this page


