# Presentation Booking System

A Next.js application designed for managing student presentation bookings. This system allows students to book 20-minute presentation slots across three weekends, with both morning and afternoon sessions available.

## Features

### Time Slot Management
- **Three Weekend Options**: Available slots spread across three weekends
- **Two Sessions Per Day**: 
  - Morning Session: 10:10 AM - 1:00 PM
  - Afternoon Session: 2:10 PM - 5:00 PM
- **20-Minute Slots**: Each presentation slot is exactly 20 minutes
- **5-Minute Breaks**: Automatic 5-minute breaks between presentations

### Booking Process
1. **Week Selection**
   - View all three available weekends
   - See total available slots per weekend
   - Past weeks are automatically disabled

2. **Day Selection**
   - Choose between Saturday or Sunday
   - View availability for each day
   - See session types (morning/afternoon)
   - Past days are automatically disabled

3. **Time Slot Selection**
   - Visual grid of all available time slots
   - Clear distinction between:
     - Available slots (green)
     - Booked slots (yellow)
     - Past slots (gray)
   - Separate morning and afternoon sessions

4. **Booking Details**
   - Required information:
     - Full Name
     - Student Number (8 digits)
   - Optional information:
     - Company Name
     - Additional Notes (max 20 characters)

### Booking Management
- **Unique Booking Codes**: Each booking receives a 4-digit code
- **Modification Options**:
  - Update company information
  - Add/modify notes
  - Cancel booking (up until the day before)
- **Cancellation Rules**: 
  - Cannot cancel on the presentation day
  - Cannot cancel past presentations

## Technical Details

### Built With
- Next.js 14 with App Router
- TypeScript for type safety
- Supabase (Postgres) for storage
- Tailwind CSS for styling
- Zustand for state management
- React Hook Form for form handling
- Zod for schema validation
- shadcn/ui components

### Key Features
- Dark/Light theme support
- Responsive design
- Real-time availability updates
- Form validation
- Error handling
- Loading states
- Accessibility features

## Getting Started

### Prerequisites
- Node.js 18.17 or higher (CI pins Node 22)
- npm package manager (the repository ships a `package-lock.json`)

### Installation
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd presentation-booking
   ```

2. Install dependencies from the lockfile:
   ```bash
   npm ci
   ```

3. Create a `.env.local` file with your Supabase project values (see `.env.example`):
   ```env
   NEXT_PUBLIC_SUPABASE_URL=
   NEXT_PUBLIC_SUPABASE_ANON_KEY=
   ```

4. Create the `bookings` table in Supabase by running [`create_bookings_table.sql`](create_bookings_table.sql) in the SQL editor.

5. Run the development server:
   ```bash
   npm run dev
   ```

6. Open [http://localhost:3000](http://localhost:3000) in your browser

## Scripts
- `npm run dev`: start the development server
- `npm run lint`: run ESLint through `next lint`
- `npm run typecheck`: run `tsc --noEmit`
- `npm run build`: production build
- `npm start`: serve the production build

CI runs on a self-hosted Windows runner (`.github/workflows/ci.yml`): `npm ci`, lint, build, typecheck.

## Environment Variables
- `NEXT_PUBLIC_SUPABASE_URL`: Supabase project URL (required)
- `NEXT_PUBLIC_SUPABASE_ANON_KEY`: Supabase anon key (required)

## Database Schema

The Supabase table is created by [`create_bookings_table.sql`](create_bookings_table.sql). Columns: `id`, `code`, `name`, `student_number`, `company`, `notes`, `slot`, `created_at`, `updated_at`.

## API Routes

### Bookings
- `GET /api/bookings`: List all bookings
- `POST /api/bookings`: Create a new booking
- `GET /api/bookings/[code]`: Get booking details
- `PATCH /api/bookings/[code]`: Update booking
- `DELETE /api/bookings/[code]`: Cancel booking

## Contributing
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License
This project is licensed under the MIT License - see the LICENSE file for details