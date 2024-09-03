# Flight Booking Model 
```swift
struct Booking {
    let bookingID: Int
    let flightID: Int
    let passengerID: Int
    let date: Date
    // Add other relevant properties
}


protocol FlightBooking {
    func bookFlight(flightID: Int, passengerID: Int, date: Date)
    func cancelBooking(bookingID: Int)
}

protocol BookingHistory {
    func viewBookingHistory(passengerID: Int) -> [Booking]
}


class Passengerguest:BookingHistory{
    func viewBookingHistory(passengerID: Int) -> [Booking] {
        return bookings.filter { $0.passengerID == passengerID }
    }
    
    
    
}

class Passenger: FlightBooking, BookingHistory {
    private var bookings: [Booking] = [] // This is a simple example; in real applications, you might fetch data from a database or network

    func bookFlight(flightID: Int, passengerID: Int, date: Date) {
        // Implementation for booking a flight
        let newBooking = Booking(bookingID: bookings.count + 1, flightID: flightID, passengerID: passengerID, date: date)
        bookings.append(newBooking)
    }

    func cancelBooking(bookingID: Int) {
        // Implementation for canceling a booking
        bookings.removeAll { $0.bookingID == bookingID }
    }

    func viewBookingHistory(passengerID: Int) -> [Booking] {
        // Filter bookings by passengerID
        return bookings.filter { $0.passengerID == passengerID }
    }
}



class PassengerViewModel {
    private let flightBookingService: FlightBooking
    private let bookingHistoryService: BookingHistory

    init(flightBookingService: FlightBooking, bookingHistoryService: BookingHistory) {
        self.flightBookingService = flightBookingService
        self.bookingHistoryService = bookingHistoryService
    }

    func bookFlight(flightID: Int, passengerID: Int, date: Date) {
        flightBookingService.bookFlight(flightID: flightID, passengerID: passengerID, date: date)
    }

    func cancelBooking(bookingID: Int) {
        flightBookingService.cancelBooking(bookingID: bookingID)
    }

    func viewBookingHistory(passengerID: Int) -> [Booking] {
        return bookingHistoryService.viewBookingHistory(passengerID: passengerID)
    }
}

let passenger = Passenger()

let viewModel = PassengerViewModel(flightBookingService: passenger, bookingHistoryService: passenger)

// Book a flight
viewModel.bookFlight(flightID: 101, passengerID: 1, date: Date())

// View booking history
let bookings = viewModel.viewBookingHistory(passengerID: 1)
for booking in bookings {
    print("Booking ID: \(booking.bookingID), Flight ID: \(booking.flightID), Date: \(booking.date)")
}


