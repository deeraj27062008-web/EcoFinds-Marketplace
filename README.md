# EcoFinds-Marketplace
Eco Finds is a sustainable second-hand marketplace where pre-loved goods find new homes. From fashion to home essentials, we make shopping eco-friendly, affordable, and unique. By promoting reuse and reducing waste, Eco Finds helps you save money while supporting a greener, circular economy
import React from 'react';
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import { Toaster } from 'react-hot-toast';
import { AuthProvider } from './hooks/useAuth';
import { Layout } from './components/Layout';
import { Home } from './pages/Home';
import { Auth } from './pages/Auth';
import { Profile } from './pages/Profile';
import { AddProduct } from './pages/AddProduct';

function App() {
  return (
    <AuthProvider>
      <Router>
        <div className="App">
          <Routes>
            <Route path="/auth" element={<Auth />} />
            <Route path="/*" element={
              <Layout>
                <Routes>
                  <Route path="/" element={<Home />} />
                  <Route path="/profile" element={<Profile />} />
                  <Route path="/add-product" element={<AddProduct />} />
                </Routes>
              </Layout>
            } />
          </Routes>
          <Toaster 
            position="top-right"
            toastOptions={{
              duration: 4000,
              style: {
                background: '#10B981',
                color: 'white',
              },
            }}
          />
        </div>
      </Router>
    </AuthProvider>
  );
}

export default App;
