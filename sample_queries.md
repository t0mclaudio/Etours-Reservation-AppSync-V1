query listReservations {
  listReservations {
    items {
      id
      email
      tour_code
      adults
      k02
      k35
      k61
      tour_date
      status
    }
  }
}

mutation createReservation {
  createReservation( input: {
    email: "tom@etours.ph"
    name: "Tom Claudio"
    contact: "09177011882"
    notes: "hello world"
    tour_code: "DST-01"
    inquiry_date: "2018-08-13T06:08:20.178Z"
    adults: 5
    k02: 0
    k35: 0
    k61: 0
    tour_date: "2018-08-13T06:08:20.178Z"
    adult_price: 2007
    k02_price: 0.0
    k35_price: 0.0
    k61_price: 0.0
    adult_total: 10035
    k02_total: 10035
    k35_total: 10035
    k61_total: 10035
    total: 10035
    downpayment: 5017.5
    balance: 5017.5
    option_date: "2018-08-13T06:08:20.178Z"
    start_date: "2018-08-13T06:08:20.178Z"
    end_date: "2018-08-13T06:08:20.178Z"
  }
  ){
    id
    date_created
  }
}